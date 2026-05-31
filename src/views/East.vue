<template>
  <div
    class="text-white min-h-screen bg-cover bg-center bg-fixed"
    style="background-image: url('https://images.unsplash.com/photo-1547471080-7cc2caa01a7e?w=1400')"
  >

    <!-- Hero -->
    <section class="bg-black/60 py-32 text-center">
      <h1 class="text-5xl font-bold text-white">Eastern Rwanda</h1>
      <p class="text-gray-300 mt-4 text-lg">Savanna, Wildlife & Wide Open Horizons</p>
    </section>

    <!-- About East -->
    <section class="bg-green-900/70 px-8 md:px-20 py-20">
      <div class="max-w-6xl mx-auto grid grid-cols-1 md:grid-cols-2 gap-16 items-center">
        <div>
          <h2 class="text-3xl font-bold text-white mb-6">About the East</h2>
          <p class="text-green-100 leading-relaxed mb-4">
            Eastern Rwanda is a stark contrast to the rest of the country — flat savanna plains stretch
            to the horizon, dotted with acacia trees and roaming wildlife. This is Rwanda's wild side,
            anchored by Akagera National Park.
          </p>
          <p class="text-green-100 leading-relaxed">
            The east is also home to vast wetlands, the Kagera River, and the tranquil shores of
            Lake Ihema — making it a paradise for birders, safari enthusiasts, and those seeking
            wide open African landscapes.
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
      <p class="text-center text-gray-300 mb-12">Places you must visit in Eastern Rwanda</p>
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
      <h2 class="text-3xl font-bold text-white mb-3">Safari in the East</h2>
      <p class="text-emerald-100 mb-8">Experience Rwanda's Big Five and endless savanna landscapes.</p>
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
  name: 'East',
  data() {
    return {
      facts: [
        { icon: '🦁', label: 'Big Five', value: 'All present in Akagera' },
        { icon: '🐘', label: 'Elephants', value: 'Reintroduced in 2016' },
        { icon: '🦒', label: 'Giraffes', value: 'Tallest in Rwanda' },
        { icon: '🐦', label: 'Birding', value: '525+ Species' },
      ],
      attractions: [
        { icon: '🦁', name: 'Akagera National Park', desc: 'Rwanda\'s only savanna park, home to lions, elephants, hippos, zebras, giraffes and over 500 bird species.' },
        { icon: '🚤', name: 'Lake Ihema Boat Safari', desc: 'Glide across the lake at sunset spotting hippos, crocodiles, and thousands of water birds up close.' },
        { icon: '🐊', name: 'Hippo & Croc Watching', desc: 'The wetlands and lakes of Akagera host massive populations of hippos and Nile crocodiles.' },
        { icon: '🌅', name: 'Savanna Game Drives', desc: 'Early morning and evening game drives through the open plains for the best wildlife sightings.' },
        { icon: '🏕️', name: 'Ruzizi Tented Lodge', desc: 'Stay in luxury tented accommodation right on the shores of Lake Ihema inside the national park.' },
        { icon: '🐦', name: 'Bird Watching', desc: 'With over 525 recorded species, Akagera is one of the finest birding destinations in Central Africa.' },
      ]
    }
  }
}
</script>