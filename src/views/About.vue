<template>
  <div class="text-white min-h-screen bg-cover bg-center bg-fixed" style="background-image: url('/src/assets/Rda.png')">

    <!-- Hero -->
    <section class="bg-black/60 py-36 text-center px-6">
      <h1 class="text-5xl font-bold mb-4">About <span class="text-yellow-300">Rwanda</span></h1>
      <p class="text-gray-300 text-lg max-w-xl mx-auto">A nation of resilience, beauty, and extraordinary spirit in the heart of Africa.</p>
    </section>

    <!-- Overview -->
    <section class="bg-green-900/70 py-20 px-6">
      <div class="max-w-5xl mx-auto grid grid-cols-1 md:grid-cols-2 gap-16 items-center">
        <div>
          <h2 class="text-3xl font-bold mb-5">The Land of a Thousand Hills</h2>
          <p class="text-green-100 leading-relaxed mb-4">Rwanda is a small but breathtaking country in Central-East Africa, bordered by Uganda, Tanzania, Burundi, and DR Congo. Despite its size, it has incredible diversity — from volcanic mountains in the north to golden savannas in the east.</p>
          <p class="text-green-100 leading-relaxed">Today Rwanda is one of Africa's fastest-growing economies, a leader in eco-tourism, and a model of cleanliness and good governance on the continent.</p>
        </div>
        <div class="grid grid-cols-2 gap-4">
          <div v-for="s in stats" :key="s.label" class="bg-black/40 border border-green-700/50 rounded-xl p-6 text-center">
            <div class="text-3xl mb-2">{{ s.icon }}</div>
            <h4 class="font-bold text-lg">{{ s.value }}</h4>
            <p class="text-green-300 text-sm mt-1">{{ s.label }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Culture -->
    <section class="bg-black/60 py-20 px-6">
      <div class="max-w-5xl mx-auto">
        <h2 class="text-3xl font-bold text-center mb-12">Culture & Traditions</h2>
        <div class="grid grid-cols-2 md:grid-cols-4 gap-5">
          <div v-for="c in cultures" :key="c.title" class="bg-black/40 border border-green-700/50 rounded-xl p-6 text-center hover:-translate-y-1 transition-transform">
            <p class="text-4xl mb-3">{{ c.icon }}</p>
            <h3 class="font-bold text-sm mb-1">{{ c.title }}</h3>
            <p class="text-gray-400 text-xs leading-relaxed">{{ c.desc }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Wildlife -->
    <section class="bg-green-900/70 py-20 px-6">
      <div class="max-w-5xl mx-auto">
        <h2 class="text-3xl font-bold text-center mb-12">Nature & Wildlife</h2>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
          <div v-for="w in wildlife" :key="w.title" class="bg-black/40 border border-green-700/50 rounded-xl p-8 text-center hover:-translate-y-1 transition-transform">
            <p class="text-5xl mb-4">{{ w.icon }}</p>
            <h3 class="font-bold text-yellow-300 text-lg mb-2">{{ w.title }}</h3>
            <p class="text-green-200 text-sm leading-relaxed">{{ w.desc }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Timeline -->
    <section class="bg-black/65 py-20 px-6">
      <div class="max-w-3xl mx-auto">
        <h2 class="text-3xl font-bold text-center mb-12">Rwanda's Journey</h2>
        <div class="relative border-l-2 border-green-600 pl-8 space-y-10">
          <div v-for="e in timeline" :key="e.year" class="relative">
            <div class="absolute -left-11 w-5 h-5 bg-green-600 rounded-full border-2 border-green-300 mt-1"></div>
            <span class="text-green-400 text-sm font-bold">{{ e.year }}</span>
            <h3 class="font-semibold text-lg mt-1">{{ e.title }}</h3>
            <p class="text-gray-400 text-sm mt-1 leading-relaxed">{{ e.desc }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA -->
    <section class="bg-emerald-900/75 text-center py-20 px-6">
      <h2 class="text-3xl font-bold mb-3">Come Experience Rwanda</h2>
      <p class="text-emerald-100 mb-8">No description does it justice — it has to be seen to be believed.</p>
      <RouterLink to="/contact"><button class="bg-white text-emerald-700 font-bold px-8 py-3 rounded-full hover:bg-green-50 transition">Plan Your Visit</button></RouterLink>
    </section>

  </div>
</template>

<script setup>
import { RouterLink } from 'vue-router'

const stats = [
  { icon: '🌍', label: 'Location',   value: 'Central Africa'              },
  { icon: '👥', label: 'Population', value: '~14 Million'                 },
  { icon: '📐', label: 'Area',       value: '26,338 km²'                  },
  { icon: '🗣️', label: 'Languages',  value: 'Kinyarwanda, English, French'},
]
const cultures = [
  { icon: '💃', title: 'Intore Dance',   desc: 'Traditional warrior dance performed at ceremonies and celebrations.' },
  { icon: '🎨', title: 'Imigongo Art',   desc: 'Unique geometric paintings made from cow dung, a UNESCO heritage art.' },
  { icon: '🧺', title: 'Basket Weaving', desc: 'Agaseke peace baskets woven with intricate patterns and symbolism.' },
  { icon: '🤝', title: 'Umuganda',       desc: 'Monthly community work day bringing all Rwandans together.' },
]
const wildlife = [
  { icon: '🦍', title: 'Mountain Gorillas', desc: "Volcanoes National Park hosts a third of the world's remaining mountain gorillas." },
  { icon: '🐘', title: 'Akagera Big Five',  desc: 'Lions, elephants, leopards, buffalo and rhinos roam the eastern savanna.' },
  { icon: '🌳', title: 'Nyungwe Forest',    desc: 'Ancient rainforest home to chimps, colobus monkeys, and over 300 bird species.' },
]
const timeline = [
  { year: 'Pre-1800s', title: 'Kingdom of Rwanda',       desc: 'Rwanda flourishes as a powerful centralized monarchy under the Mwami (King).' },
  { year: '1884',      title: 'Colonial Era',            desc: 'Rwanda becomes part of German East Africa, later transferred to Belgian control.' },
  { year: '1962',      title: 'Independence',            desc: 'Rwanda gains independence from Belgium on July 1st, 1962.' },
  { year: '1994',      title: 'Genocide Against Tutsi',  desc: 'Approximately 800,000 Tutsi and moderate Hutu are killed in 100 days.' },
  { year: '2000s',     title: 'Rebuilding & Growth',     desc: "Rwanda emerges as one of Africa's fastest-growing and most stable economies." },
  { year: 'Today',     title: 'Vision 2050',             desc: 'Rwanda aims to become a high-income country and top African tourism destination.' },
]
</script>