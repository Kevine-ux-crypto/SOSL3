<script setup></script>

<template>
  <!-- Home Page -->
  <section
    class="relative h-screen bg-cover bg-center flex items-center justify-center text-white"
    style="background-image: url('/src/assets/Rda.png');"
  >
    <!-- Overlay -->
    <div class="absolute inset-0 bg-black/50"></div>

    <!-- Content -->
    <div class="relative text-center px-4">
      <h1 class="text-5xl md:text-6xl font-bold mb-4 tracking-wide">
        Welcome to Rwanda
      </h1>

      <p class="text-xl text-green-300 mb-6">
        The Land of a Thousand Hills
      </p>

      <!-- Buttons -->
      <div class="flex justify-center gap-4">
        <button
          class="bg-green-600 hover:bg-green-700 px-5 py-2 rounded-full transition"
        >
          Explore
        </button>

        <button
          class="border border-white hover:bg-white hover:text-black px-5 py-2 rounded-full transition"
        >
          Discover
        </button>
      </div>

      <!-- Small Cards -->
      <div class="mt-10 flex justify-center gap-4 flex-wrap">
        <div class="bg-white/20 backdrop-blur-sm px-30 py-10 rounded-xl">
         Land of a thousand hills!<br>
         Live where every moment iss breathtaking.<br>
         Enjoy beautiful landscapes and views!
        </div>

        <div class="bg-white/20 backdrop-blur-sm px-30 py-10 rounded-xl">
         Peaceful beautiful country!<br>
         Secure to visit for anyone to visit.<br>
         Very amazing to live in!
        </div>

        <div class="bg-white/20 backdrop-blur-sm px-30 py-10 rounded-xl">
          Come explore us! <br>
          And discover the beauty of our country.<br>
          Find beautiful places to try and visit!
        </div>
      </div>
    </div>
  </section>
</template>