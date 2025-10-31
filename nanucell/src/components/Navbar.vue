<template>
  <nav
    class="sticky top-0 flex justify-between items-center bg-white/60 backdrop-blur-md text-purple-900 px-8 py-4 shadow-lg z-50"
  >
    <!-- Logo -->
    <div class="text-2xl font-bold bg-logo bg-no-repeat bg-contain w-48 h-14"></div>

    <!-- Navigation Links -->
    <ul class="flex space-x-6 items-center text-lg">
      <li>
        <a href="#packages" :class="linkClass('packages')" @click.prevent="scrollToSection('packages')">Packages</a>
      </li>
      <li>
        <a href="#products" :class="linkClass('products')" @click.prevent="scrollToSection('products')">More Products</a>
      </li>
      <li>
        <a href="#reviews" :class="linkClass('reviews')" @click.prevent="scrollToSection('reviews')">Reviews</a>
      </li>
      <li>
        <a href="#contacts" :class="linkClass('contacts')" @click.prevent="scrollToSection('contacts')">Contacts</a>
      </li>

      <!-- Shop Now Button -->
      <div class="bg-purple-900 p-3 rounded-lg transition-all duration-300 hover:scale-110 hover:shadow-xl hover:bg-purple-800 active:scale-95">
        <li>
          <button @click="showShopModal = true" class="text-yellow-300 font-semibold animate-pulse hover:animate-none">
            Shop Now!
          </button>
        </li>
      </div>
    </ul>
  </nav>

  <!-- Teleport modal to body so it's not constrained by the sticky nav -->
  <teleport to="body">
    <ShopNowModal
      v-if="showShopModal"
      @close="showShopModal = false"
      @submit="handleShopSubmit"
    />
  </teleport>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'
import ShopNowModal from './ShopNowModal.vue'

const active = ref('')
const showShopModal = ref(false)

function handleShopSubmit(payload) {
  // Example: you can POST to your Django endpoint here.
  // For now we just log; replace with fetch/axios as needed.
  console.log('Order submitted payload:', payload)

  // Example (commented):
  // fetch('/api/orders/', {
  //   method: 'POST',
  //   headers: { 'Content-Type': 'application/json' },
  //   body: JSON.stringify(payload)
  // }).then(r => r.json()).then(res => { ... }).catch(err => { ... })
}

// Smooth scroll to section id
function scrollToSection(id) {
  const el = document.getElementById(id)
  if (el) {
    el.scrollIntoView({ behavior: 'smooth', block: 'start' })
    active.value = id
  } else {
    window.scrollTo({ top: 0, behavior: 'smooth' })
    active.value = ''
  }
}

function linkClass(id) {
  return [
    'hover:text-yellow-400',
    'font-medium',
    active.value === id ? 'text-[rgb(105,30,104)] font-semibold' : ''
  ].join(' ')
}

let observer = null
onMounted(() => {
  const sections = ['packages', 'products', 'reviews', 'contacts']
  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((e) => {
        if (e.isIntersecting) active.value = e.target.id
      })
    },
    { root: null, rootMargin: '-40% 0px -40% 0px', threshold: 0 }
  )
  sections.forEach((id) => {
    const el = document.getElementById(id)
    if (el) observer.observe(el)
  })
})

onBeforeUnmount(() => {
  if (observer) observer.disconnect()
})
</script>
