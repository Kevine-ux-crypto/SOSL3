<template>
  <div
    class="text-white min-h-screen bg-cover bg-center bg-fixed"
    style="background-image: url('https://images.unsplash.com/photo-1605649487212-47bdab064df7?w=1400')"
  >

    <!-- Hero -->
    <section class="bg-black/60 py-32 text-center">
      <h1 class="text-5xl font-bold text-white">Northern Rwanda</h1>
      <p class="text-gray-300 mt-4 text-lg">Land of Volcanoes, Gorillas & Misty Mountains</p>
    </section>

    <!-- About North -->
    <section class="bg-green-900/70 px-8 md:px-20 py-20">
      <div class="max-w-6xl mx-auto grid grid-cols-1 md:grid-cols-2 gap-16 items-center">
        <div>
          <h2 class="text-3xl font-bold text-white mb-6">About the North</h2>
          <p class="text-green-100 leading-relaxed mb-4">
            Northern Rwanda is dominated by the dramatic Virunga mountain range, home to some of Africa's
            most awe-inspiring landscapes. This region is world-famous for mountain gorilla trekking
            in Volcanoes National Park.
          </p>
          <p class="text-green-100 leading-relaxed">
            Beyond gorillas, the north offers golden monkey tracking, twin lake hikes, and the rich
            culture of the Musanze area — a perfect base for exploring the region.
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
      <p class="text-center text-gray-300 mb-12">Places you must visit in Northern Rwanda</p>
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
      <h2 class="text-3xl font-bold text-white mb-3">Explore the North</h2>
      <p class="text-emerald-100 mb-8">Book your gorilla trekking permit and mountain adventure today.</p>
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
  name: 'North',
  data() {
    return {
      facts: [
        { icon: '🌋', label: 'Volcanoes', value: '5 Dormant Peaks' },
        { icon: '🦍', label: 'Gorillas', value: 'Mountain Gorillas' },
        { icon: '🏔️', label: 'Highest Peak', value: 'Mt Karisimbi 4,507m' },
        { icon: '🌿', label: 'Main Park', value: 'Volcanoes Nat. Park' },
      ],
      attractions: [
        { icon: '🦍', name: 'Gorilla Trekking', desc: 'Trek through misty forest to encounter endangered mountain gorillas in their natural habitat — a once-in-a-lifetime experience.' },
        { icon: '🐒', name: 'Golden Monkey Tracking', desc: 'Follow troops of playful golden monkeys through the bamboo forests of the Virunga slopes.' },
        { icon: '🌋', name: 'Mt Bisoke Hike', desc: 'Hike to the crater lake atop Mt Bisoke for breathtaking panoramic views of the Virunga range.' },
        { icon: '💧', name: 'Twin Lakes (Burera & Ruhondo)', desc: 'Two stunningly beautiful lakes nestled among volcanic hills, perfect for boat trips and photography.' },
        { icon: '🏛️', name: 'Musanze Caves', desc: 'Explore ancient lava tube caves stretching over 2km, rich with history and unique rock formations.' },
        { icon: '🌿', name: 'Dian Fossey Tomb', desc: 'Visit the grave of the legendary primatologist Dian Fossey, located deep within Volcanoes National Park.' },
      ]
    }
  }
}
</script>