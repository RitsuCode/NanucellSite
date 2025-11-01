<template>
  <section id="packages" class="py-16 relative overflow-hidden bg-gradient-to-br from-purple-50 via-white to-yellow-50">
    <!-- Animated background dots -->
    <div class="absolute inset-0 w-full h-full z-0">
      <div class="absolute w-20 h-20 bg-purple-200/50 rounded-full animate-float" style="top: 10%; left: 20%"></div>
      <div class="absolute w-24 h-24 bg-yellow-200/50 rounded-full animate-float-delayed" style="top: 60%; left: 80%"></div>
      <div class="absolute w-28 h-28 bg-purple-100/50 rounded-full animate-float" style="top: 80%; left: 10%"></div>
      <div class="absolute w-32 h-32 bg-yellow-100/50 rounded-full animate-float-delayed" style="top: 30%; left: 60%"></div>
      <!-- New larger dots -->
      <div class="absolute w-36 h-36 bg-purple-100/30 rounded-full animate-float-slow" style="top: 40%; left: 30%"></div>
      <div class="absolute w-40 h-40 bg-yellow-100/30 rounded-full animate-float-slower" style="top: 15%; left: 70%"></div>
      <div class="absolute w-44 h-44 bg-purple-200/30 rounded-full animate-float-slowest" style="top: 70%; left: 40%"></div>
    </div>

    <div class="container mx-auto px-4 relative z-10">
      <h2 class="text-4xl font-bold text-[rgb(105,30,104)] text-center mb-12">
        Choose from our packages that's right for you!
      </h2>

      <div class="flex flex-col md:flex-row gap-8 justify-center items-stretch">
        <!-- Business Package -->
        <div class="bg-[rgb(221,223,224)] backdrop-blur-sm rounded-xl p-8 shadow-lg transition-all duration-300 hover:scale-110 hover:shadow-xl border-2 border-[rgb(105,30,104)]">
          <h3 class="text-2xl font-bold text-[rgb(105,30,104)] mb-2">Business Package</h3>
          <div class="flex items-baseline gap-2 mb-6">
            <span class="text-4xl font-bold text-[rgb(105,30,104)]">11,940 PHP</span>
            <span class="text-lg text-[rgb(105,30,104)]">only!</span>
          </div>
          <ul class="mb-8 space-y-2 text-[rgb(105,30,104)]">
            <li>• Get 1 Bottle of Ultima Stem Plus</li>
            <li>• Lifetime membership</li>
            <li>• Get 25% discount on all products</li>
          </ul>
          <button class="w-full bg-yellow-400 text-white py-3 rounded-lg font-bold transition-all duration-300 hover:scale-110 hover:shadow-xl hover:bg-yellow-400 active:scale-95">
            BUY NOW
          </button>
        </div>

        <!-- Executive Package -->
        <div class="bg-[rgb(221,223,224)] backdrop-blur-sm rounded-xl p-8 shadow-lg transition-all duration-300 hover:scale-110 hover:shadow-xl border-2 border-[rgb(105,30,104)] relative">
          <div class="absolute -top-4 right-4 bg-yellow-400 text-white px-4 py-1 rounded-full text-sm font-bold shadow-lg">
            MOST POPULAR
          </div>
          <h3 class="text-2xl font-bold text-[rgb(105,30,104)] mb-2">Executive Package</h3>
          <div class="flex items-baseline gap-2 mb-6">
            <span class="text-4xl font-bold text-[rgb(105,30,104)]">47,760 PHP</span>
            <span class="text-lg text-[rgb(105,30,104)]">only!</span>
          </div>
          <ul class="mb-8 space-y-2 text-[rgb(105,30,104)]">
            <li>• Get 4 Bottles of Ultima Stem Plus</li>
            <li>• Lifetime membership</li>
            <li>• Get 25% discount on all products</li>
          </ul>
          <button class="w-full bg-yellow-400 text-white py-3 rounded-lg font-bold transition-all duration-300 hover:scale-110 hover:shadow-xl hover:bg-yellow-400 active:scale-95">
            BUY NOW
          </button>
        </div>

        <!-- Elite Package -->
        <div class="bg-[rgb(221,223,224)] backdrop-blur-sm rounded-xl p-8 shadow-lg transition-all duration-300 hover:scale-110 hover:shadow-xl border-2 border-[rgb(105,30,104)]">
          <h3 class="text-2xl font-bold text-[rgb(105,30,104)] mb-2">Elite Package</h3>
          <div class="flex items-baseline gap-2 mb-6">
            <span class="text-4xl font-bold text-[rgb(105,30,104)]">149,000 PHP</span>
            <span class="text-lg text-[rgb(105,30,104)]">only!</span>
          </div>
          <ul class="mb-8 space-y-2 text-[rgb(105,30,104)]">
            <li>• Get 12 Bottles of Ultima Stem Plus</li>
            <li>• 1 Berberine</li>
            <li>• 1 BerryOrac</li>
            <li>• Lifetime membership</li>
            <li>• Get 25% discount on all products</li>
          </ul>
          <button class="w-full bg-yellow-400 text-white py-3 rounded-lg font-bold transition-all duration-300 hover:scale-110 hover:shadow-xl hover:bg-yellow-400 active:scale-95">
            BUY NOW
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Packages'
}
</script>

<style scoped>
@keyframes float {
  0%, 100% {
    transform: translateY(0) translateX(0);
  }
  50% {
    transform: translateY(-20px) translateX(10px);
  }
}

@keyframes float-delayed {
  0%, 100% {
    transform: translateY(0) translateX(0);
  }
  50% {
    transform: translateY(20px) translateX(-10px);
  }
}

@keyframes float-slow {
  0%, 100% {
    transform: translateY(0) translateX(0);
  }
  50% {
    transform: translateY(-30px) translateX(15px);
  }
}

@keyframes float-slower {
  0%, 100% {
    transform: translateY(0) translateX(0);
  }
  50% {
    transform: translateY(25px) translateX(-20px);
  }
}

@keyframes float-slowest {
  0%, 100% {
    transform: translateY(0) translateX(0);
  }
  50% {
    transform: translateY(-35px) translateX(-25px);
  }
}

.animate-float {
  animation: float 8s ease-in-out infinite;
}

.animate-float-delayed {
  animation: float-delayed 9s ease-in-out infinite;
}

.animate-float-slow {
  animation: float-slow 12s ease-in-out infinite;
}

.animate-float-slower {
  animation: float-slower 15s ease-in-out infinite;
}

.animate-float-slowest {
  animation: float-slowest 18s ease-in-out infinite;
}

/* Add subtle pulse to the Most Popular tag */
@keyframes subtle-pulse {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.05); }
}

.bg-yellow-400 {
  animation: subtle-pulse 2s infinite;
}
</style>