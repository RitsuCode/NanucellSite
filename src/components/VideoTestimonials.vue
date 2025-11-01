<template>
  <section class="py-3 bg-white">
    <div class="container mx-auto px-4">
      <!-- simplified layout: two columns, video smaller (1/3) and carousel larger (2/3) -->
      <div class="flex flex-col lg:flex-row gap-8 items-start mr-10">
        <!-- Left: Video (copied player structure from DoctorsSection) -->
        <div class="flex flex-col lg:flex-row items-center justify-center gap-8">
        <!-- Left: single Doctors PNG (takes 2/3 on large screens) -->

        <!-- Right: Video (takes 1/3 on large screens) -->
        <div class="w-full lg:w-2/5 flex items-start justify-items-center mt-2 shadow-lg">
          <video
            ref="videoEl"
            :src="video"
            class="w-full rounded-lg shadow-lg bg-black"
            controls
            playsinline
          ></video>
        </div>
      </div>

        <!-- Carousel column (larger, centered content) -->
        <div class="w-full lg:w-2/3 flex items-start justify-center p-3 mr-10 border-2 rounded-lg border-gray-200">
          <div
            class="relative bg-white rounded-lg shadow-lg overflow-hidden w-full max-w-4xl"
            @mouseenter="pauseAuto"
            @mouseleave="startAuto"
          >
            <div class="relative h-80 sm:h-96 flex items-center justify-center bg-[rgb(221,223,224)]">
              <template v-if="images.length">
                <img
                  :src="images[current]"
                  :alt="imageAlts[current] || `slide-${current}`"
                  class="max-h-full max-w-full object-contain transition-opacity duration-700"
                />
              </template>
              <template v-else>
                <div class="text-gray-400">No images found</div>
              </template>

              <button v-if="images.length" @click="prev" class="absolute left-2 top-1/2 -translate-y-1/2 bg-white/80 rounded-full p-2 shadow hover:scale-105" aria-label="Previous">‹</button>
              <button v-if="images.length" @click="next" class="absolute right-2 top-1/2 -translate-y-1/2 bg-white/80 rounded-full p-2 shadow hover:scale-105" aria-label="Next">›</button>
            </div>

            <div class="px-4 py-3 bg-white flex items-center gap-3 overflow-x-auto justify-center shadow-md border-2 border-gray-200 rounded-md">
              <template v-for="(img, i) in images" :key="i">
                <button
                  @click="goTo(i)"
                  class="flex-none rounded-md overflow-hidden border-2 transition-transform"
                  :class="i === current ? 'border-[rgb(105,30,104)] scale-105' : 'border-transparent'"
                >
                  <img :src="img" :alt="imageAlts[i] || `thumb-${i}`" class="w-20 h-20 object-cover" loading="lazy" />
                </button>
              </template>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import video from '../assets/videos/Marites Antenor.mp4'

// import images
const modules = import.meta.glob('../assets/images/reviews/*.{png,jpg,jpeg,webp}', { eager: true })
const images = []
const imageAlts = []
for (const path of Object.keys(modules)) {
  const mod = modules[path]
  const src = mod && mod.default ? mod.default : (typeof mod === 'string' ? mod : null)
  if (!src) continue
  images.push(src)
  const fname = path.split('/').pop().replace(/\.[^/.]+$/, '')
  imageAlts.push(decodeURIComponent(fname).replace(/[-_]/g, ' '))
}

// carousel state
const current = ref(0)
const intervalMs = 4000
let timer = null

function next() { if (!images.length) return; current.value = (current.value + 1) % images.length }
function prev() { if (!images.length) return; current.value = (current.value - 1 + images.length) % images.length }
function goTo(i) { if (!images.length) return; current.value = i }
function startAuto() { if (timer || images.length <= 1) return; timer = setInterval(next, intervalMs) }
function pauseAuto() { if (!timer) return; clearInterval(timer); timer = null }

// video player state
const videoEl = ref(null)
const playing = ref(false)

function playVideo() {
  const v = videoEl.value
  if (!v) return
  v.play().catch(() => {})
  playing.value = true
}

onMounted(() => {
  startAuto()
  const v = videoEl.value
  if (v) {
    v.addEventListener('play', () => (playing.value = true))
    v.addEventListener('pause', () => (playing.value = false))
    v.addEventListener('ended', () => (playing.value = false))
  }
})

onUnmounted(() => {
  pauseAuto()
  const v = videoEl.value
  if (v) {
    v.removeEventListener('play', () => (playing.value = true))
    v.removeEventListener('pause', () => (playing.value = false))
    v.removeEventListener('ended', () => (playing.value = false))
  }
})
</script>

<style scoped>
/* small niceties */
::-webkit-scrollbar { height: 8px; }
::-webkit-scrollbar-thumb { background: rgba(0,0,0,0.12); border-radius: 999px; }
</style>