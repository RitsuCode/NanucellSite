<template>
  <section id="reviews" class="py-5 bg-[rgb(105,30,104)]">
    <div class="container mx-auto px-4">
      <h2 class="text-4xl font-bold text-white mb-12 text-center">Customer Reviews</h2>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-6 justify-items-center">
        <!-- Review Card 1 -->
        <div class="bg-white p-6 w-80 h-80 rounded-lg shadow-lg transition-all duration-300 hover:scale-105 flex flex-col">
          <div class="flex text-yellow-400 text-4xl mb-2">
            ★★★★<span class="text-gray-300">★</span>
          </div>
          <div class="text-gray-600 mb-2">4 out of 5</div>
          <div class="flex-grow overflow-y-auto">
            <p class="text-gray-800 mb-4">
              "Wala na yung mass sa left breast ko... Totally nawala na.. Yan ang result ng MRI ko khpon lang. Laking tulong ng Ultima Stem Plus..."
            </p>
          </div>
          <p class="text-purple-800 italic mt-auto">- Anonymous, Philippines</p>
        </div>

        <!-- Review Card 2 -->
        <div class="bg-white p-6 w-80 h-80 rounded-lg shadow-lg transition-all duration-300 hover:scale-105 flex flex-col">
          <div class="flex text-yellow-400 text-4xl mb-2">
            ★★★★★
          </div>
          <div class="text-gray-600 mb-2">5 out of 5</div>
          <div class="flex-grow overflow-y-auto">
            <p class="text-gray-800 mb-4">
              "After two weeks of taking Ultima Stem Plus with Berberine, mas malakas at mas bata ang pakiramdam ko—hindi na kailangan ng hospitalization."
            </p>
          </div>
          <p class="text-purple-800 italic mt-auto">- Willie Del Rosario, Seattle, USA</p>
        </div>

        <!-- Review Card 3 -->
        <div class="bg-white p-6 w-80 h-80 rounded-lg shadow-lg transition-all duration-300 hover:scale-105 flex flex-col">
          <div class="flex text-yellow-400 text-4xl mb-2">
            ★★★★★
          </div>
          <div class="text-gray-600 mb-2">5 out of 5</div>
          <div class="flex-grow overflow-y-auto">
            <p class="text-gray-800 mb-4">
              "Nag take din po ako 2 tabs each... 3 times a day... napansin ko po na sumasabay na sa ihi ko yong stones na durog. Nag undergo po kasi ako ng procedure break kidney stones last 3 months ago."
            </p>
          </div>
          <p class="text-purple-800 italic mt-auto">- Anonymous, Philippines</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'CustomerReviews'
}
</script>