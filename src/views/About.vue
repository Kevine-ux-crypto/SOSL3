<template>
  <section
    class="relative h-screen w-full bg-cover bg-center flex items-center justify-center"
    style="background-image: url('/src/assets/VR.png');"
  >
    <!-- Overlay -->
    <div class="absolute inset-0 bg-black/50"></div>

    <!-- Content -->
    <div class="relative text-center px-4 text-white">
      <h1 class="text-5xl md:text-6xl font-bold mb-4">
        DISCOVER RWANDA!
      </h1>

      <p class="text-lg text-green-300 mb-6">
        Discover culture, nature and beauty
      </p>

      <button
        class="bg-green-600 hover:bg-green-700 px-6 py-2 rounded-full transition"
      >
        Learn More
      </button>
    </div>
  </section>
</template>