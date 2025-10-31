<template>
  <section id="products" class="py-12 bg-white">
    <div class="container mx-auto px-4">
      <h2 class="text-3xl font-bold text-purple-800 mb-6">Shop More Nanucell Products!</h2>

      <div v-if="loading" class="text-gray-500">Loading products...</div>
      <div v-else-if="products.length === 0" class="text-gray-500">No product images found in src/assets/images/products</div>

      <div v-else class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-4 gap-6">
        <article
          v-for="(product, idx) in products"
          :key="idx"
          class="bg-white rounded-md p-3 shadow-sm flex flex-col"
        >
          <div class="w-full h-48 flex items-center justify-center bg-gray-50 rounded shadow-md overflow-hidden">
            <img
              :src="product.src"
              :alt="product.name"
              class="w-full h-full object-contain"
              loading="lazy"
            />
          </div>

          <h3 class="mt-3 text-purple-800 font-semibold break-words">{{ product.name }}</h3>
          <p class="text-sm text-gray-500">{{ product.intake }}</p>

          <div class="mt-3 flex items-center justify-between">
            <div class="text-lg font-bold text-gray-800">{{ product.price }}</div>
            <button
              class="bg-purple-800 text-white text-sm px-3 py-1 rounded transition hover:bg-purple-700 active:scale-95"
              type="button"
            >
              Add to Cart
            </button>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

/*
  EDITABLE SECTION:
  - Update the array below to change intake / price / display name for each product.
  - "file" should match the filename (without extension) in src/assets/images/products.
  - Example: an image at src/assets/images/products/Ultima Stem Plus.png -> file: 'Ultima Stem Plus'
*/
const editableProducts = [
  // Example entries — replace these with your actual filenames & metadata
  { file: 'BerryOrac', name: 'BerryOrac', intake: '3.1g / 12 Sachets', price: '1,608 PHP' },
  { file: 'Berberine', name: 'Berberine', intake: '500mg / capsule', price: '5,950 PHP' },
  { file: 'Bloom Gluta', name: 'Bloom Gluta', intake: '500mg / capsule', price: '1,804 PHP' },
  { file: 'Carvacrol', name: 'Carvacrol', intake: '500mg / softgel', price: '1,795 PHP' },
  { file: 'Equi C', name: 'Equi C', intake: '250mg / tablet', price: '1,625 PHP' },
  { file: 'Nucleanse', name: 'Nucleanse', intake: '3.1g / sachet', price: '2,220 PHP' },
  { file: 'Spirulina', name: 'Spirulina', intake: '250mg / tablet', price: '1,698 PHP' },
  // Add or remove entries as needed
]

const loading = ref(true)
const products = ref([])

try {
  // eager load images from products folder
  const modules = import.meta.glob('../assets/images/products/*.{png,jpg,jpeg}', { eager: true })

  // map filename -> url
  const imagesMap = Object.entries(modules).reduce((acc, [path, mod]) => {
    const fname = path.split('/').pop().replace(/\.[^/.]+$/, '')
    const src = mod && mod.default ? mod.default : (typeof mod === 'string' ? mod : null)
    if (src) acc[fname] = src
    return acc
  }, {})

  // Build final products list:
  // 1) Start from editableProducts (preserve order if you want)
  // 2) Then append any images not defined in editableProducts using defaults
  const seen = new Set()
  const list = []

  for (const e of editableProducts) {
    const src = imagesMap[e.file]
    if (!src) {
      // If the image referenced by editableProducts is missing, still include entry if you want:
      if (e.name && e.file) {
        list.push({
          src: '', // no image found
          name: e.name,
          intake: e.intake || '500mg / capsule',
          price: e.price || '5,950 PHP'
        })
      }
      continue
    }
    seen.add(e.file)
    list.push({
      src,
      name: e.name || e.file,
      intake: e.intake || '500mg / capsule',
      price: e.price || '5,950 PHP'
    })
  }

  // Append remaining images not listed in editableProducts
  for (const [fname, src] of Object.entries(imagesMap)) {
    if (seen.has(fname)) continue
    list.push({
      src,
      name: fname.replace(/[-_]/g, ' '),
      intake: '500mg / capsule',
      price: '5,950 PHP'
    })
  }

  products.value = list
} catch (err) {
  // eslint-disable-next-line no-console
  console.error('Error loading product images:', err)
} finally {
  loading.value = false
}
</script>

<style scoped>
/* keep product name wrapping neat */
h3 { word-wrap: break-word; }
</style>