<template>
  <div
    class="text-white min-h-screen bg-cover bg-center bg-fixed"
    style="background-image: url('https://images.unsplash.com/photo-1516026672322-bc52d61a55d5?w=1400')"
  >

    <!-- Hero -->
    <section class="bg-black/60 py-32 text-center">
      <h1 class="text-5xl font-bold text-white">Photo Gallery</h1>
      <p class="text-gray-300 mt-4 text-lg">Rwanda through the lens</p>
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

    <!-- Hero Grid -->
    <section class="bg-green-900/70 px-8 md:px-20 pb-20">

      <!-- Featured + side grid block (every 5 images) -->
      <div
        v-for="(chunk, chunkIndex) in chunkedImages"
        :key="chunkIndex"
        class="mb-6"
      >
        <!-- If chunk has at least 1 image -->
        <div v-if="chunk.length > 0" class="grid gap-3"
          :class="chunk.length === 1 ? 'grid-cols-1' : 'grid-cols-3'"
          style="grid-template-rows: auto;"
        >
          <!-- Featured large image (first in chunk) -->
          <div
            class="relative rounded-2xl overflow-hidden cursor-pointer group"
            :class="chunk.length > 1 ? 'col-span-2 row-span-2' : 'col-span-3'"
            style="min-height: 420px;"
            @click="openLightbox(chunk[0])"
          >
            <!-- Replace with <img :src="chunk[0].src" class="w-full h-full object-cover" /> -->
            <div class="w-full h-full bg-green-950/80 flex items-center justify-center" style="min-height: 420px;">
              <div class="text-center">
                <div class="text-8xl mb-4 opacity-80">{{ chunk[0].icon }}</div>
                <p class="text-white font-semibold text-lg">{{ chunk[0].caption }}</p>
                <p class="text-green-300 text-sm mt-1">{{ chunk[0].location }}</p>
              </div>
            </div>
            <!-- Hover overlay -->
            <div class="absolute inset-0 bg-black/40 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-center justify-center">
              <div class="bg-green-600/80 rounded-full p-4">
                <svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0zM10 7v3m0 0v3m0-3h3m-3 0H7"/>
                </svg>
              </div>
            </div>
            <!-- Caption bar -->
            <div class="absolute bottom-0 left-0 right-0 bg-gradient-to-t from-black/70 to-transparent p-5">
              <p class="text-white font-bold text-xl">{{ chunk[0].caption }}</p>
              <p class="text-green-300 text-sm">{{ chunk[0].location }}</p>
            </div>
          </div>

          <!-- Side smaller images (2nd to 5th in chunk) -->
          <div
            v-for="(image, i) in chunk.slice(1, 5)"
            :key="image.id"
            class="relative rounded-2xl overflow-hidden cursor-pointer group"
            style="min-height: 200px;"
            @click="openLightbox(image)"
          >
            <!-- Replace with <img :src="image.src" class="w-full h-full object-cover" /> -->
            <div class="w-full h-full bg-green-900/60 flex items-center justify-center" style="min-height: 200px;">
              <div class="text-center px-3">
                <div class="text-5xl mb-2 opacity-80">{{ image.icon }}</div>
                <p class="text-white text-xs font-medium">{{ image.caption }}</p>
              </div>
            </div>
            <!-- Hover overlay -->
            <div class="absolute inset-0 bg-black/40 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-center justify-center">
              <div class="bg-green-600/80 rounded-full p-3">
                <svg class="w-5 h-5 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0zM10 7v3m0 0v3m0-3h3m-3 0H7"/>
                </svg>
              </div>
            </div>
            <!-- Caption bar -->
            <div class="absolute bottom-0 left-0 right-0 bg-gradient-to-t from-black/70 to-transparent p-3">
              <p class="text-white font-semibold text-sm">{{ image.caption }}</p>
              <p class="text-green-300 text-xs">{{ image.location }}</p>
            </div>
          </div>

        </div>
      </div>

      <!-- Empty state -->
      <div v-if="filteredImages.length === 0" class="text-center py-20">
        <p class="text-green-200 text-lg">No images in this category yet.</p>
      </div>
    </section>

    <!-- Lightbox -->
    <Teleport to="body">
      <div
        v-if="selectedImage"
        class="fixed inset-0 bg-black/90 z-50 flex items-center justify-center px-4"
        @click.self="closeLightbox"
      >
        <div class="relative max-w-2xl w-full">
          <!-- Close button -->
          <button
            @click="closeLightbox"
            class="absolute -top-12 right-0 text-white hover:text-green-400 transition text-3xl font-light"
          >✕</button>

          <!-- Image placeholder -->
          <div class="bg-green-950 rounded-2xl overflow-hidden" style="min-height: 400px;">
            <div class="w-full flex items-center justify-center" style="min-height: 400px;">
              <div class="text-center p-10">
                <div class="text-9xl mb-6 opacity-80">{{ selectedImage.icon }}</div>
                <!-- Replace with: <img :src="selectedImage.src" class="w-full object-cover" /> -->
              </div>
            </div>
          </div>

          <!-- Caption -->
          <div class="mt-4 px-2">
            <div class="flex items-center justify-between">
              <div>
                <h3 class="text-white font-bold text-xl">{{ selectedImage.caption }}</h3>
                <p class="text-green-400 text-sm mt-1">📍 {{ selectedImage.location }}</p>
              </div>
              <span class="text-xs bg-green-700/60 text-green-200 px-3 py-1 rounded-full">
                {{ selectedImage.category }}
              </span>
            </div>
          </div>

          <!-- Prev / Next -->
          <div class="flex justify-between mt-6">
            <button
              @click="prevImage"
              :disabled="currentIndex === 0"
              class="bg-green-700 hover:bg-green-600 disabled:opacity-30 text-white px-6 py-2 rounded-full transition text-sm font-medium"
            >← Previous</button>
            <button
              @click="nextImage"
              :disabled="currentIndex === filteredImages.length - 1"
              class="bg-green-700 hover:bg-green-600 disabled:opacity-30 text-white px-6 py-2 rounded-full transition text-sm font-medium"
            >Next →</button>
          </div>
        </div>
      </div>
    </Teleport>

    <!-- CTA -->
    <section class="bg-emerald-900/75 text-center py-20 px-8">
      <h2 class="text-3xl font-bold text-white mb-3">Want to See It for Yourself?</h2>
      <p class="text-emerald-100 mb-8">Book a tour and create your own Rwanda memories.</p>
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
  name: 'Images',
  data() {
    return {
      selectedImage: null,
      currentIndex: 0,
      activeCategory: 'All',
      categories: ['All', 'Wildlife', 'Landscape', 'Culture', 'City'],
      images: [
        { id: 1,  icon: '🦍', caption: 'Mountain Gorilla',    location: 'Volcanoes National Park', category: 'Wildlife'  },
        { id: 2,  icon: '🌋', caption: 'Virunga Volcanoes',    location: 'Northern Rwanda',         category: 'Landscape' },
        { id: 3,  icon: '🌿', caption: 'Nyungwe Rainforest',   location: 'Southern Rwanda',         category: 'Landscape' },
        { id: 4,  icon: '🦁', caption: 'Lion at Sunrise',      location: 'Akagera National Park',   category: 'Wildlife'  },
        { id: 5,  icon: '🌊', caption: 'Lake Kivu Sunset',     location: 'Western Rwanda',          category: 'Landscape' },
        { id: 6,  icon: '🏙️', caption: 'Kigali Skyline',       location: 'Kigali City',             category: 'City'      },
        { id: 7,  icon: '🐒', caption: 'Golden Monkey',        location: 'Volcanoes National Park', category: 'Wildlife'  },
        { id: 8,  icon: '🍵', caption: 'Tea Plantation',       location: 'Gisakura, South Rwanda',  category: 'Landscape' },
        { id: 9,  icon: '🥁', caption: 'Traditional Dance',    location: 'Southern Rwanda',         category: 'Culture'   },
        { id: 10, icon: '🛍️', caption: 'Kimironko Market',     location: 'Kigali City',             category: 'Culture'   },
        { id: 11, icon: '🐘', caption: 'Elephant Herd',        location: 'Akagera National Park',   category: 'Wildlife'  },
        { id: 12, icon: '🚴', caption: 'Congo Nile Trail',     location: 'Western Rwanda',          category: 'Landscape' },
      ]
    }
  },
  computed: {
    filteredImages() {
      if (this.activeCategory === 'All') return this.images
      return this.images.filter(img => img.category === this.activeCategory)
    },
    chunkedImages() {
      const chunks = []
      for (let i = 0; i < this.filteredImages.length; i += 5) {
        chunks.push(this.filteredImages.slice(i, i + 5))
      }
      return chunks
    }
  },
  methods: {
    openLightbox(image) {
      this.currentIndex = this.filteredImages.findIndex(img => img.id === image.id)
      this.selectedImage = image
    },
    closeLightbox() {
      this.selectedImage = null
    },
    prevImage() {
      if (this.currentIndex > 0) {
        this.currentIndex--
        this.selectedImage = this.filteredImages[this.currentIndex]
      }
    },
    nextImage() {
      if (this.currentIndex < this.filteredImages.length - 1) {
        this.currentIndex++
        this.selectedImage = this.filteredImages[this.currentIndex]
      }
    }
  }
}
</script>