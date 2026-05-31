<template>
  <div class="text-white min-h-screen bg-cover bg-center bg-fixed" style="background-image: url('/src/assets/Rda.png')">

    <!-- Hero -->
    <section class="bg-black/50 h-screen flex items-center justify-center text-center px-4">
      <div>
        <h1 class="text-5xl md:text-6xl font-bold mb-4">Welcome to Rwanda</h1>
        <p class="text-xl text-green-300 mb-8">The Land of a Thousand Hills</p>
        <div class="flex justify-center gap-4 mb-14">
          <RouterLink to="/services"><button class="bg-green-600 hover:bg-green-500 px-7 py-3 rounded-full font-semibold transition">Explore</button></RouterLink>
          <RouterLink to="/about"><button class="border border-white hover:bg-white hover:text-black px-7 py-3 rounded-full font-semibold transition">Discover</button></RouterLink>
        </div>
        <div class="flex justify-center gap-4 flex-wrap text-sm">
          <div v-for="card in heroCards" :key="card" class="bg-white/20 backdrop-blur-sm px-8 py-6 rounded-xl max-w-xs leading-relaxed">{{ card }}</div>
        </div>
      </div>
    </section>

    <!-- Why Rwanda -->
    <section class="bg-green-900/70 py-20 px-8">
      <h2 class="text-3xl font-bold text-center mb-3">Why Visit Rwanda?</h2>
      <p class="text-center text-green-200 mb-12">A destination unlike any other in Africa</p>
      <div class="max-w-6xl mx-auto grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
        <div v-for="r in reasons" :key="r.title" class="bg-black/40 border border-green-700/50 rounded-xl p-6 text-center hover:-translate-y-1 transition-transform">
          <div class="text-4xl mb-4">{{ r.icon }}</div>
          <h3 class="font-semibold mb-2">{{ r.title }}</h3>
          <p class="text-gray-400 text-sm">{{ r.desc }}</p>
        </div>
      </div>
    </section>

    <!-- Regions -->
    <section class="bg-black/60 py-20 px-8">
      <h2 class="text-3xl font-bold text-center mb-3">Explore by Region</h2>
      <p class="text-center text-gray-300 mb-12">Five unique regions, five unforgettable experiences</p>
      <div class="max-w-6xl mx-auto grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-5 gap-4">
        <RouterLink v-for="r in regions" :key="r.name" :to="r.path" class="group relative rounded-2xl overflow-hidden" style="min-height:280px">
          <div class="w-full h-full flex items-end p-5" :style="`background:${r.bg}; min-height:280px`">
            <div class="absolute inset-0 flex items-center justify-center">
              <span class="text-6xl opacity-50 group-hover:opacity-70 group-hover:scale-110 transition-all">{{ r.icon }}</span>
            </div>
            <div class="relative z-10">
              <h3 class="font-bold text-lg">{{ r.name }}</h3>
              <p class="text-green-200 text-xs mt-1">{{ r.tagline }}</p>
            </div>
          </div>
        </RouterLink>
      </div>
    </section>

    <!-- Services -->
    <section class="bg-green-900/70 py-20 px-8">
      <h2 class="text-3xl font-bold text-center mb-3">What We Offer</h2>
      <p class="text-center text-green-200 mb-12">Everything for a perfect Rwanda trip</p>
      <div class="max-w-5xl mx-auto grid grid-cols-2 md:grid-cols-3 gap-5">
        <div v-for="s in services" :key="s.title" class="bg-black/40 border border-green-700/50 rounded-xl p-5 flex items-center gap-4 hover:-translate-y-1 transition-transform">
          <span class="text-3xl">{{ s.icon }}</span>
          <div>
            <h3 class="font-semibold text-sm">{{ s.title }}</h3>
            <p class="text-gray-400 text-xs mt-1">{{ s.desc }}</p>
          </div>
        </div>
      </div>
      <div class="text-center mt-10">
        <RouterLink to="/services"><button class="bg-green-600 hover:bg-green-500 font-bold px-8 py-3 rounded-full transition">View All Services</button></RouterLink>
      </div>
    </section>

    <!-- CTA -->
    <section class="bg-emerald-900/75 text-center py-24 px-8">
      <h2 class="text-4xl font-bold mb-4">Ready for Your Rwanda Adventure?</h2>
      <p class="text-emerald-100 text-lg mb-8 max-w-xl mx-auto">Let us help you plan the trip of a lifetime to the Land of a Thousand Hills.</p>
      <RouterLink to="/contact"><button class="bg-white text-emerald-700 font-bold px-10 py-4 rounded-full hover:bg-green-50 transition text-lg">Start Planning</button></RouterLink>
    </section>

  </div>
</template>

<script setup>
import { RouterLink } from 'vue-router'

const heroCards = [
  '🏔️ Land of a thousand hills!\nLive where every moment is breathtaking.\nEnjoy beautiful landscapes and views!',
  '🕊️ Peaceful beautiful country!\nSecure to visit for anyone.\nVery amazing to live in!',
  '🌍 Come explore us!\nDiscover the beauty of our country.\nFind beautiful places to visit!',
]
const reasons = [
  { icon: '🦍', title: 'Gorilla Trekking',   desc: 'One of only three countries where you can trek mountain gorillas in the wild.' },
  { icon: '🌿', title: 'Eco-Tourism Leader', desc: 'Rwanda leads Africa in sustainable, responsible eco-tourism practices.' },
  { icon: '🏙️', title: 'Cleanest City',      desc: 'Kigali is consistently ranked the cleanest city in all of Africa.' },
  { icon: '🛡️', title: 'Safest Destination', desc: 'One of the safest countries in Africa for solo and family travelers.' },
]
const regions = [
  { name: 'Kigali', path: '/kigali', icon: '🏙️', tagline: 'The vibrant capital',     bg: 'linear-gradient(135deg,#1a3a1a,#0d2a0d)' },
  { name: 'North',  path: '/north',  icon: '🌋', tagline: 'Volcanoes & gorillas',    bg: 'linear-gradient(135deg,#1a2a10,#0a1f0a)' },
  { name: 'South',  path: '/south',  icon: '🌿', tagline: 'Forests & royal culture', bg: 'linear-gradient(135deg,#0d2a1a,#052015)' },
  { name: 'East',   path: '/east',   icon: '🦁', tagline: 'Safari & savanna',        bg: 'linear-gradient(135deg,#2a1a0a,#1a0f05)' },
  { name: 'West',   path: '/west',   icon: '🌊', tagline: 'Lake Kivu & trails',      bg: 'linear-gradient(135deg,#0a1a2a,#051020)' },
]
const services = [
  { icon: '🦍', title: 'Safari & Wildlife',  desc: 'Gorilla trekking & game drives' },
  { icon: '🚗', title: 'Transport',           desc: 'Transfers & guided road trips'  },
  { icon: '🏨', title: 'Accommodation',       desc: 'Lodges, camps & city hotels'    },
  { icon: '🥁', title: 'Cultural Tours',      desc: 'Villages, dance & traditions'   },
  { icon: '🏔️', title: 'Adventure',           desc: 'Hiking, cycling & zip-lining'   },
  { icon: '📷', title: 'Photography Tours',   desc: 'Guided landscape photo trips'   },
]
</script>