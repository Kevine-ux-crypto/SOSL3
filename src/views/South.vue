<template>
  <div
    class="text-white min-h-screen bg-cover bg-center bg-fixed"
    style="background-image: url('https://images.unsplash.com/photo-1580746738099-5b6b6f28e3e7?w=1400')"
  >

    <!-- Hero -->
    <section class="bg-black/60 py-32 text-center">
      <h1 class="text-5xl font-bold text-white">Southern Rwanda</h1>
      <p class="text-gray-300 mt-4 text-lg">Culture, Tea Gardens & Stunning Natural Beauty</p>
    </section>

    <!-- About South -->
    <section class="bg-green-900/70 px-8 md:px-20 py-20">
      <div class="max-w-6xl mx-auto grid grid-cols-1 md:grid-cols-2 gap-16 items-center">
        <div>
          <h2 class="text-3xl font-bold text-white mb-6">About the South</h2>
          <p class="text-green-100 leading-relaxed mb-4">
            Southern Rwanda is a land of rolling green hills, vast tea plantations, and deep cultural
            roots. Home to the ancient royal court of Nyanza and the remarkable Nyungwe Forest,
            the south is a treasure trove for nature lovers and history enthusiasts alike.
          </p>
          <p class="text-green-100 leading-relaxed">
            The region also boasts the famous Huye (Butare) city, known as Rwanda's intellectual capital,
            housing the country's oldest university and national museum.
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
      <p class="text-center text-gray-300 mb-12">Places you must visit in Southern Rwanda</p>
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
      <h2 class="text-3xl font-bold text-white mb-3">Discover the South</h2>
      <p class="text-emerald-100 mb-8">From canopy walks to royal palaces — the south has it all.</p>
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
  name: 'South',
  data() {
    return {
      facts: [
        { icon: '🌿', label: 'Nyungwe Forest', value: 'Oldest Rainforest' },
        { icon: '🍵', label: 'Tea Plantations', value: 'Gisakura & Shagasha' },
        { icon: '👑', label: 'Royal History', value: 'Nyanza Royal Palace' },
        { icon: '🎓', label: 'Education', value: "Rwanda's Intellectual Hub" },
      ],
      attractions: [
        { icon: '🌿', name: 'Nyungwe Forest National Park', desc: 'One of Africa\'s oldest rainforests, home to chimpanzees, colobus monkeys, and over 300 bird species.' },
        { icon: '🚶', name: 'Canopy Walkway', desc: 'Walk 70 meters above the forest floor on a thrilling suspension bridge with breathtaking treetop views.' },
        { icon: '👑', name: 'Nyanza Royal Palace', desc: 'Explore the reconstructed traditional palace of the Rwandan kings, complete with the famous royal cattle.' },
        { icon: '🏛️', name: 'National Museum of Rwanda', desc: 'Located in Huye, this is the finest museum in Rwanda, showcasing the country\'s art, culture and history.' },
        { icon: '🍵', name: 'Gisakura Tea Estate', desc: 'Tour the lush green tea plantations and learn the full process from leaf to cup while enjoying scenic views.' },
        { icon: '💧', name: 'Rusumo Falls', desc: 'Dramatic waterfalls on the Tanzanian border — a powerful and scenic natural landmark worth the journey.' },
      ]
    }
  }
}
</script>