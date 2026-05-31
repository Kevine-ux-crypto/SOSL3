<template>
  <div
    class="text-white min-h-screen bg-cover bg-center bg-fixed"
    style="background-image: url('https://images.unsplash.com/photo-1504432842672-1a79f78e4084?w=1400')"
  >

    <!-- Hero -->
    <section class="bg-black/60 py-32 text-center">
      <h1 class="text-5xl font-bold text-white">Western Rwanda</h1>
      <p class="text-gray-300 mt-4 text-lg">Lake Kivu, Congo Nile Trail & Breathtaking Scenery</p>
    </section>

    <!-- About West -->
    <section class="bg-green-900/70 px-8 md:px-20 py-20">
      <div class="max-w-6xl mx-auto grid grid-cols-1 md:grid-cols-2 gap-16 items-center">
        <div>
          <h2 class="text-3xl font-bold text-white mb-6">About the West</h2>
          <p class="text-green-100 leading-relaxed mb-4">
            Western Rwanda is defined by the magnificent Lake Kivu — one of Africa's Great Lakes —
            stretching along the border with the Democratic Republic of Congo. The western highlands
            offer some of the most spectacular scenery in all of Rwanda.
          </p>
          <p class="text-green-100 leading-relaxed">
            The region is also home to the famous Congo Nile Trail, a world-class cycling and hiking
            route, as well as Kibuye, Rubavu (Gisenyi), and countless scenic islands dotting the lake.
          </p>
        </div>
        <div class="grid grid-cols-2 gap-4">
          <div v-for="fact in facts" :key="fact.label" class="bg-black/40 border border-green-700/50 rounded-xl p-6 text-center">
            <div class="text-3xl mb-2">{{ fact.icon }}</div>
            <h4 class="text-white font-semibold">{{ fact.label }}</h4>
            <p class="text-green-200 text-sm mt-1">{{ fact.value }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Top Attractions -->
    <section class="bg-black/60 px-8 md:px-20 py-20">
      <h2 class="text-3xl font-bold text-white text-center mb-2">Top Attractions</h2>
      <p class="text-center text-gray-300 mb-12">Places you must visit in Western Rwanda</p>
      <div class="max-w-6xl mx-auto grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
        <div
          v-for="place in attractions"
          :key="place.name"
          class="bg-black/40 border border-green-700/50 rounded-xl p-6 hover:-translate-y-1 transition-transform duration-200"
        >
          <div class="text-3xl mb-3">{{ place.icon }}</div>
          <h3 class="text-lg font-semibold text-white mb-2">{{ place.name }}</h3>
          <p class="text-sm text-gray-300 leading-relaxed">{{ place.desc }}</p>
        </div>
      </div>
    </section>

    <!-- CTA -->
    <section class="bg-emerald-900/75 text-center py-20 px-8">
      <h2 class="text-3xl font-bold text-white mb-3">Explore the West</h2>
      <p class="text-emerald-100 mb-8">Sail on Lake Kivu and ride the famous Congo Nile Trail.</p>
      <router-link to="/contact">
        <button class="bg-white text-emerald-700 font-bold px-8 py-3 rounded-full hover:bg-green-50 transition">
          Get In Touch
        </button>
      </router-link>
    </section>

  </div>
</template>

<script>
export default {
  name: 'West',
  data() {
    return {
      facts: [
        { icon: '🌊', label: 'Lake Kivu', value: "One of Africa's Great Lakes" },
        { icon: '🚴', label: 'Congo Nile Trail', value: '227km Scenic Route' },
        { icon: '🏝️', label: 'Islands', value: 'Napoleon & Idjwi Island' },
        { icon: '🌋', label: 'Border', value: 'DR Congo Border' },
      ],
      attractions: [
        { icon: '🌊', name: 'Lake Kivu', desc: 'Swim, kayak, or sail on one of Africa\'s most beautiful lakes, surrounded by green hills and dotted with islands.' },
        { icon: '🚴', name: 'Congo Nile Trail', desc: 'A 227km world-class trail for cyclists and hikers running along the dramatic shores of Lake Kivu.' },
        { icon: '🏖️', name: 'Rubavu (Gisenyi)', desc: 'A lively lakeside town with beach bars, resorts, and a buzzing nightlife right on the shores of Lake Kivu.' },
        { icon: '⛪', name: 'Kibuye (Karongi)', desc: 'A peaceful, scenic town perfect for boat trips, island visits, and relaxing lakeside getaways.' },
        { icon: '🏝️', name: 'Napoleon Island', desc: 'A small island on Lake Kivu home to thousands of fruit bats — a spectacular wildlife experience at dusk.' },
        { icon: '♨️', name: 'Rubavu Hot Springs', desc: 'Natural volcanic hot springs near the DRC border, a unique geological wonder and relaxing soak.' },
      ]
    }
  }
}
</script>