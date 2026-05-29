<script setup>
import { RouterLink } from 'vue-router'
</script>

<template>
  <div>

    <!-- Hero -->
    <section class="bg-green-800 text-white text-center py-20 px-6"
    style="background-image: url('/src/assets/Rda.png')">
      <h1 class="text-5xl font-bold mb-4">About <span class="text-yellow-300">Rwanda</span></h1>
      <p class="text-green-200 text-lg max-w-xl mx-auto">
        A nation of resilience, beauty, and extraordinary spirit in the heart of Africa.
      </p>
    </section>

    <!-- Overview -->
    <section class="py-16 px-6 max-w-4xl mx-auto">
      <h2 class="text-3xl font-bold text-green-900 mb-5">The Land of a Thousand Hills</h2>
      <p class="text-gray-600 leading-relaxed mb-4">
        Rwanda is a small but breathtaking country in Central-East Africa, bordered by Uganda, Tanzania,
        Burundi, and DR Congo. Despite its size, it has incredible diversity — from volcanic mountains
        in the north to golden savannas in the east.
      </p>
      <p class="text-gray-600 leading-relaxed">
        Today Rwanda is one of Africa's fastest-growing economies, a leader in eco-tourism,
        and a model of cleanliness and good governance on the continent.
      </p>

      
    </section>

    

    <!-- Culture -->
    <section class="py-16 px-6 max-w-4xl mx-auto">
      <h2 class="text-3xl font-bold text-green-900 text-center mb-10">Culture & Traditions</h2>
      <div class="grid grid-cols-2 md:grid-cols-4 gap-5">
        <div class="bg-green-50 rounded-xl p-5 text-center">
          <p class="text-3xl mb-2">💃</p>
          <h3 class="font-bold text-green-900 text-sm">Intore Dance</h3>
          <p class="text-gray-500 text-xs mt-1">Traditional warrior dance.</p>
        </div>
        <div class="bg-yellow-50 rounded-xl p-5 text-center">
          <p class="text-3xl mb-2">🎨</p>
          <h3 class="font-bold text-green-900 text-sm">Imigongo Art</h3>
          <p class="text-gray-500 text-xs mt-1">Unique geometric paintings.</p>
        </div>
        <div class="bg-blue-50 rounded-xl p-5 text-center">
          <p class="text-3xl mb-2">🧺</p>
          <h3 class="font-bold text-green-900 text-sm">Basket Weaving</h3>
          <p class="text-gray-500 text-xs mt-1">Agaseke peace baskets.</p>
        </div>
        <div class="bg-orange-50 rounded-xl p-5 text-center">
          <p class="text-3xl mb-2">🤝</p>
          <h3 class="font-bold text-green-900 text-sm">Umuganda</h3>
          <p class="text-gray-500 text-xs mt-1">Monthly community work day.</p>
        </div>
      </div>
    </section>

    <!-- Wildlife -->
    <section class="bg-green-800 text-white py-16 px-6">
      <div class="max-w-4xl mx-auto">
        <h2 class="text-3xl font-bold text-center mb-10">Nature & Wildlife</h2>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
          <div class="bg-green-700 rounded-xl p-6 text-center">
            <p class="text-4xl mb-3">🦍</p>
            <h3 class="font-bold text-yellow-300 mb-1">Mountain Gorillas</h3>
            <p class="text-green-200 text-sm">Volcanoes National Park hosts a third of the world's mountain gorillas.</p>
          </div>
          <div class="bg-green-700 rounded-xl p-6 text-center">
            <p class="text-4xl mb-3">🐘</p>
            <h3 class="font-bold text-yellow-300 mb-1">Akagera Big Five</h3>
            <p class="text-green-200 text-sm">Lions, elephants, leopards, buffalo and rhinos in the east.</p>
          </div>
          <div class="bg-green-700 rounded-xl p-6 text-center">
            <p class="text-4xl mb-3">🌳</p>
            <h3 class="font-bold text-yellow-300 mb-1">Nyungwe Forest</h3>
            <p class="text-green-200 text-sm">Ancient rainforest home to chimps, monkeys, and 300 bird species.</p>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA -->
    <section class="bg-yellow-400 text-center py-14 px-6">
      <h2 class="text-3xl font-bold text-green-900 mb-3">Come Experience Rwanda</h2>
      <p class="text-green-800 mb-6">No description does it justice — it has to be seen to be believed.</p>
      <RouterLink to="/contact" class="bg-green-900 text-white font-bold px-8 py-3 rounded-full hover:bg-green-800">
        Plan Your Visit
      </RouterLink>
    </section>

  </div>
</template>