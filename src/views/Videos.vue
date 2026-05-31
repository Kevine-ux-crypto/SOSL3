<template>
  <div
    class="text-white min-h-screen bg-cover bg-center bg-fixed"
    style="background-image: url('https://images.unsplash.com/photo-1516026672322-bc52d61a55d5?w=1400')"
  >

    <!-- Hero -->
    <section class="bg-black/60 py-32 text-center">
      <h1 class="text-5xl font-bold text-white">Video Gallery</h1>
      <p class="text-gray-300 mt-4 text-lg">Experience Rwanda in motion</p>
    </section>

    <!-- Filter Buttons -->
    <section class="bg-green-900/70 py-8 px-8 text-center">
      <div class="flex flex-wrap justify-center gap-3">
        <button
          v-for="category in categories"
          :key="category"
          @click="activeCategory = category"
          :class="activeCategory === category
            ? 'bg-green-500 text-white'
            : 'bg-black/40 text-green-200 border border-green-700/50 hover:bg-green-700/50'"
          class="px-5 py-2 rounded-full text-sm font-medium transition duration-200"
        >
          {{ category }}
        </button>
      </div>
    </section>

    <!-- Video Grid -->
    <section class="bg-green-900/70 px-8 md:px-20 pb-20">
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8 max-w-6xl mx-auto">
        <div
          v-for="video in filteredVideos"
          :key="video.id"
          class="bg-black/40 border border-green-700/50 rounded-xl overflow-hidden hover:-translate-y-1 transition-transform duration-200"
        >
          <!-- Thumbnail placeholder — swap div for <video> or <iframe> later -->
          <div
            class="h-48 bg-gray-800/70 flex items-center justify-center relative cursor-pointer group"
            @click="openModal(video)"
          >
            <div class="text-5xl">{{ video.icon }}</div>
            <div class="absolute inset-0 bg-black/40 flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity duration-200">
              <div class="bg-green-600 rounded-full w-14 h-14 flex items-center justify-center">
                <span class="text-white text-2xl ml-1">▶</span>
              </div>
            </div>
          </div>

          <!-- Video Info -->
          <div class="p-5">
            <span class="text-xs bg-green-700/60 text-green-200 px-3 py-1 rounded-full">{{ video.category }}</span>
            <h3 class="text-white font-semibold text-base mt-3 mb-1">{{ video.title }}</h3>
            <p class="text-gray-400 text-sm leading-relaxed">{{ video.desc }}</p>
            <div class="flex items-center gap-2 mt-3">
              <span class="text-green-400 text-xs">⏱ {{ video.duration }}</span>
              <span class="text-gray-600 text-xs">•</span>
              <span class="text-gray-400 text-xs">📍 {{ video.location }}</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Empty state -->
      <div v-if="filteredVideos.length === 0" class="text-center py-20">
        <p class="text-green-200 text-lg">No videos in this category yet.</p>
      </div>
    </section>

    <!-- Video Modal -->
    <div
      v-if="selectedVideo"
      class="fixed inset-0 bg-black/85 z-50 flex items-center justify-center px-4"
      @click.self="closeModal"
    >
      <div class="bg-gray-900 border border-green-700/50 rounded-2xl p-8 max-w-lg w-full text-center">
        <!-- Swap this placeholder with <video> or <iframe> when you have real files -->
        <div class="h-52 bg-gray-800 rounded-xl flex items-center justify-center mb-6">
          <div class="text-center">
            <div class="text-6xl mb-3">{{ selectedVideo.icon }}</div>
            <p class="text-green-300 text-sm">Video player coming soon</p>
            <p class="text-gray-500 text-xs mt-1">Replace with your video file</p>
          </div>
        </div>
        <h3 class="text-white font-bold text-xl mb-2">{{ selectedVideo.title }}</h3>
        <p class="text-gray-400 text-sm mb-1">{{ selectedVideo.location }}</p>
        <p class="text-green-300 text-xs mb-6">{{ selectedVideo.duration }}</p>
        <button
          @click="closeModal"
          class="bg-green-600 hover:bg-green-500 text-white font-bold px-8 py-2 rounded-full transition"
        >
          Close
        </button>
      </div>
    </div>

    <!-- CTA -->
    <section class="bg-emerald-900/75 text-center py-20 px-8">
      <h2 class="text-3xl font-bold text-white mb-3">Inspired by What You Saw?</h2>
      <p class="text-emerald-100 mb-8">Let us plan your perfect Rwanda adventure.</p>
      <router-link to="/contact">
        <button class="bg-white text-emerald-700 font-bold px-8 py-3 rounded-full hover:bg-green-50 transition">
          Plan Your Trip
        </button>
      </router-link>
    </section>

  </div>
</template>

<script>
export default {
  name: 'Videos',
  data() {
    return {
      selectedVideo: null,
      activeCategory: 'All',
      categories: ['All', 'Wildlife', 'Adventure', 'Culture', 'City'],
      videos: [
        { id: 1, icon: '🦍', title: 'Gorilla Trekking Experience',  desc: 'Follow rangers deep into the forest for a life-changing encounter with mountain gorillas.',  duration: '4:32', location: 'Volcanoes NP',  category: 'Wildlife'   },
        { id: 2, icon: '🌊', title: 'Sailing on Lake Kivu',         desc: 'A peaceful boat journey across one of Africa\'s most beautiful and serene lakes.',           duration: '3:15', location: 'Lake Kivu',    category: 'Adventure'  },
        { id: 3, icon: '🦁', title: 'Akagera Safari Drive',         desc: 'Morning game drive through the open savanna spotting lions, elephants and giraffes.',        duration: '6:48', location: 'Akagera NP',  category: 'Wildlife'   },
        { id: 4, icon: '🏙️', title: 'Kigali City Tour',             desc: 'Explore the clean streets, vibrant markets, and rich culture of Rwanda\'s capital city.',    duration: '5:20', location: 'Kigali',       category: 'City'       },
        { id: 5, icon: '🌿', title: 'Nyungwe Canopy Walk',          desc: 'Walk 70 meters above the forest floor on a breathtaking suspension bridge.',                 duration: '2:55', location: 'Nyungwe Forest',category: 'Adventure'  },
        { id: 6, icon: '🥁', title: 'Traditional Dance & Culture',  desc: 'Vibrant Rwandan cultural performances, traditional ceremonies and local crafts.',            duration: '3:40', location: 'Southern Rwanda',category: 'Culture'   },
        { id: 7, icon: '🚴', title: 'Congo Nile Trail Cycling',     desc: 'Ride the legendary 227km trail along the dramatic shores of Lake Kivu.',                     duration: '7:10', location: 'Western Rwanda', category: 'Adventure'  },
        { id: 8, icon: '🐒', title: 'Golden Monkey Tracking',       desc: 'Follow playful golden monkeys through the bamboo forests of the Virunga slopes.',            duration: '4:05', location: 'Volcanoes NP',  category: 'Wildlife'   },
        { id: 9, icon: '🛍️', title: 'Kimironko Market Experience',  desc: 'Explore Kigali\'s most colorful market — fabrics, crafts, food and authentic local life.',   duration: '3:22', location: 'Kigali',        category: 'Culture'    },
      ]
    }
  },
  computed: {
    filteredVideos() {
      if (this.activeCategory === 'All') return this.videos
      return this.videos.filter(v => v.category === this.activeCategory)
    }
  },
  methods: {
    openModal(video) {
      this.selectedVideo = video
    },
    closeModal() {
      this.selectedVideo = null
    }
  }
}
</script>