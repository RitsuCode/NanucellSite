<template>
  <section class="bg-gray-100">
    <div class="container mx-auto">
      <div class="flex flex-col md:flex-row items-center justify-between bg-[rgb(221,223,224)] rounded-lg shadow-lg overflow-hidden">
        <!-- Left side with image -->
        <div class="w-full md:w-1/2 p-8">
          <h2 class="text-6xl font-bold text-yellow-400 drop-shadow-[0_4px_3px_rgba(0,0,0,0.5)] mb-4">Best Seller!</h2>
          <div class="w-full lg:w-3/4 ml-28 flex items-center justify-center">
              <img 
                src="../assets/images/UltimaStemPack.png" 
                alt="Ultima Stem Pack" 
                class="w-full object-contain"
              />
          </div>
        </div>

        <!-- Right side with content -->
        <div class="w-full md:w-1/2 p-8">
          <h3 class="text-6xl font-bold mb-4 animate-gradient bg-gradient-to-r from-yellow-400 via-purple-800 to-yellow-600 bg-[length:200%_auto] text-transparent bg-clip-text drop-shadow-xl">
            Buy 2 Bottles now and get 25% off on your next purchase!
          </h3>
          
          <div class="flex items-baseline gap-2 mb-6">
            <span class="text-4xl font-bold animate-gradient bg-gradient-to-r from-yellow-400 via-purple-800 to-yellow-600 bg-[length:200%_auto] text-transparent bg-clip-text drop-shadow-xl">23,800 PHP</span>
            <span class="text-xl bg-gradient-to-r from-yellow-400 via-purple-800 to-yellow-600 bg-[length:200%_auto] text-transparent bg-clip-text drop-shadow-xl">only!</span>
          </div>

          <button class="bg-yellow-400 text-white px-8 py-3 rounded-lg text-4xl font-bold 
                       transition-all duration-300 hover:scale-110 hover:shadow-xl hover:bg-yellow-400 active:scale-95 shadow-xl">
            BUY NOW
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'BestSeller'
}
</script>

<style>
@keyframes gradient {
  0% {
    background-position: 0% 50%;
  }
  100% {
    background-position: 100% 50%;
  }
}

.animate-gradient {
  animation: gradient 3s linear infinite alternate;
}
</style>