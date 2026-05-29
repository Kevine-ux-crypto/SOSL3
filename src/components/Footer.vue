<script setup lang="ts">
import { RouterLink } from 'vue-router'
</script>

<template>
  <footer class="bg-green-800 text-white px-8 py-5 relative inset-x-0 bottom-0 w-full">

    <div class="flex flex-wrap justify-between gap-5">

      <div>
        <h3 class="text-yellow-300 font-bold text-lg mb-3">
          Tembera U Rwanda
        </h3>
        <p class="text-sm text-green-200">
          Discover the beauty of the Land of a Thousand Hills!
        </p>
      </div>

      <!-- Quick Links -->
      <div>
        <h3 class="text-yellow-300 font-bold text-lg mb-3">
          Quick Links
        </h3>
        <ul class="space-y-2 text-sm">
          <li><RouterLink to="/" class="hover:text-yellow-300">Home</RouterLink></li>
          <li><RouterLink to="/about" class="hover:text-yellow-300">About</RouterLink></li>
          <li><RouterLink to="/contact" class="hover:text-yellow-300">Contact</RouterLink></li>
          <li><RouterLink to="/service" class="hover:text-yellow-300">Services</RouterLink></li>
        </ul>
      </div>

      <!-- Destinations -->
      <div>
        <h3 class="text-yellow-300 font-bold text-lg mb-3">
          Destinations
        </h3>
        <ul class="space-y-2 text-sm">
          <li><RouterLink to="/kigali" class="hover:text-yellow-300">Kigali City</RouterLink></li>
          <li><RouterLink to="/north" class="hover:text-yellow-300">North</RouterLink></li>
          <li><RouterLink to="/south" class="hover:text-yellow-300">South</RouterLink></li>
          <li><RouterLink to="/west" class="hover:text-yellow-300">West</RouterLink></li>
          <li><RouterLink to="/east" class="hover:text-yellow-300">East</RouterLink></li>
        </ul>
      </div>

      <!-- Contacts -->
      <div>
        <h3 class="text-yellow-300 font-bold text-lg mb-3">
          Contacts
        </h3>
        <ul class="space-y-2 text-sm">
          <li class="text-green-200">sos@93gmail.com</li>
          <li class="text-green-200">+250792769283</li>
          <li class="text-green-200">Kigali, Rwanda</li>
        </ul>
      </div>

    </div>

    <!-- Copyright -->
    <div class="border-t border-green-600 mt-8 pt-4 text-sm text-green-200">
      <p class="text-center">
        © 2025 Visit Rwanda. All Rights Reserved
      </p>
    </div>

  </footer>
</template>