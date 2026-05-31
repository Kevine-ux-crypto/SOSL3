<template>
  <div
    class="text-white min-h-screen bg-cover bg-center bg-fixed"
    style="background-image: url('https://images.unsplash.com/photo-1516026672322-bc52d61a55d5?w=1400')"
  >

    <!-- Hero - dark black overlay -->
    <section class="bg-yellow-500/50 py-32 text-center">
      <h1 class="text-5xl font-bold text-white">Our Services</h1>
      <p class="text-gray-300 mt-4 text-lg">Everything you need for an unforgettable Rwanda experience</p>
    </section>

    <!-- Services Cards - green overlay -->
    <section class="bg-green-900/70 px-16 py-20">
      <h2 class="text-center text-3xl font-bold text-white mb-2">What We Offer</h2>
      <p class="text-center text-green-200 mb-12">Tailored services for every type of traveler</p>
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
        <div
          v-for="service in services"
          :key="service.title"
          class="bg-black/40 border border-green-700/50 rounded-xl p-8 text-center hover:-translate-y-1 transition-transform duration-200"
        >
          <div class="text-4xl mb-4">{{ service.icon }}</div>
          <h3 class="text-lg font-semibold text-white mb-3">{{ service.title }}</h3>
          <p class="text-sm text-green-100 leading-relaxed">{{ service.desc }}</p>
        </div>
      </div>
    </section>

    <!-- CTA - emerald overlay -->
    <section class="bg-emerald-800/75 text-center py-20 px-8">
      <h2 class="text-3xl font-bold text-white mb-3">Ready to Plan Your Trip?</h2>
      <p class="text-emerald-100 mb-8">Contact us today and let our team craft the perfect Rwanda itinerary for you.</p>
      <router-link to="/contact">
        <button class="bg-white text-emerald-700 font-bold px-8 py-3 rounded-full hover:bg-green-50 transition">
          Contact Us
        </button>
      </router-link>
    </section>

  </div>
</template>

<script>
export default {
  name: 'Services',
  data() {
    return {
      services: [
        { icon: '🦍', title: 'Safari & Wildlife Tours', desc: "Track mountain gorillas in Volcanoes National Park and explore Akagera's savanna wildlife." },
        { icon: '🥁', title: 'Cultural Experiences', desc: 'Immerse yourself in Rwandan traditions, dance, crafts, and community village visits.' },
        { icon: '🚗', title: 'Transport & Transfers', desc: 'Comfortable airport pickups, inter-city transfers, and private guided road trips.' },
        { icon: '🏨', title: 'Accommodation', desc: 'From luxury lodges to eco-friendly camps — we find the perfect stay for your budget.' },
        { icon: '🏔️', title: 'Adventure Activities', desc: 'Hiking, zip-lining, boat safaris on Lake Kivu, and Congo Nile Trail cycling tours.' },
        { icon: '📷', title: 'Photography Tours', desc: "Guided tours specifically designed for photographers capturing Rwanda's stunning landscapes." },
      ]
    }
  }
}
</script>