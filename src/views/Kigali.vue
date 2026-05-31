<template>
  <div
    class="text-white min-h-screen bg-cover bg-center bg-fixed"
    style="background-image: url('/src/assets/cbn.png')"
  >

    <!-- Hero -->
    <section class="bg-black/60 py-32 text-center">
      <h1 class="text-5xl font-bold text-white">Kigali</h1>
      <p class="text-gray-300 mt-4 text-lg">The Heart of Rwanda — Clean, Vibrant & Modern</p>
    </section>

    <!-- About Kigali -->
    <section class="bg-green-900/70 px-8 md:px-20 py-20">
      <div class="max-w-6xl mx-auto grid grid-cols-1 md:grid-cols-2 gap-16 items-center">
        <div>
          <h2 class="text-3xl font-bold text-white mb-6">About Kigali</h2>
          <p class="text-green-100 leading-relaxed mb-4">
            Kigali is one of Africa's cleanest and most modern capitals. Nestled among rolling hills,
            the city blends a rich cultural heritage with rapid urban development, making it a truly
            unique destination on the continent.
          </p>
          <p class="text-green-100 leading-relaxed">
            From vibrant markets and world-class restaurants to moving memorials and contemporary art
            galleries, Kigali offers an experience that is both deeply reflective and excitingly forward-looking.
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
      <p class="text-center text-gray-300 mb-12">Places you must visit in Kigali</p>
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
      <h2 class="text-3xl font-bold text-white mb-3">Plan Your Kigali Visit</h2>
      <p class="text-emerald-100 mb-8">Let us help you explore the best of Rwanda's capital city.</p>
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
  name: 'Kigali',
  data() {
    return {
      facts: [
        { icon: '🌍', label: 'Capital City', value: 'Since 1962' },
        { icon: '👥', label: 'Population', value: '~1.4 Million' },
        { icon: '🌡️', label: 'Climate', value: 'Mild & Pleasant' },
        { icon: '✈️', label: 'Airport', value: 'Kigali Intl Airport' },
      ],
      attractions: [
        { icon: '🕊️', name: 'Kigali Genocide Memorial', desc: 'A powerful memorial and museum dedicated to the victims of the 1994 genocide, offering a sobering and important history.' },
        { icon: '🎨', name: 'Inema Arts Center', desc: 'A vibrant contemporary art gallery showcasing Rwanda\'s most talented artists through exhibitions and live performances.' },
        { icon: '🛍️', name: 'Kimironko Market', desc: 'Kigali\'s largest and most colorful market — perfect for fabrics, crafts, fresh produce, and local street food.' },
        { icon: '🍽️', name: 'Nyamirambo', desc: 'The city\'s most lively neighborhood, packed with local restaurants, bars, mosques, and authentic Rwandan culture.' },
        { icon: '🦁', name: 'Kigali Zoo', desc: 'Home to a variety of African wildlife, a great family-friendly visit in the heart of the city.' },
        { icon: '🏛️', name: 'Presidential Palace Museum', desc: 'Explore the former residence of President Habyarimana, preserved as a fascinating historical museum.' },
      ]
    }
  }
}
</script>