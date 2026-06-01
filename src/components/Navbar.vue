<script setup lang="ts">
import { RouterLink } from 'vue-router'
import { ref, provide } from 'vue'

const languages = [
  { code: 'en', label: 'EN', full: 'English' },
  { code: 'fr', label: 'FR', full: 'Français' },
  { code: 'rw', label: 'RW', full: 'Kinyarwanda' },
]

const currentLang = ref(languages[0])
provide('lang', currentLang)

function setLang(lang: typeof languages[0]) {
  currentLang.value = lang
}
</script>

<template>
  <nav class="bg-green-800 text-white px-8 py-4 flex items-center justify-between shadow-lg w-full z-50">
    <img src="../assets/logo3.png" class="h-10 w-auto">

    <ul class="flex gap-8 text-sm font-medium w-full px-5 justify-end items-center">
      <li><RouterLink to="/" class="hover:text-yellow-300">Home</RouterLink></li>
      <li><RouterLink to="/about" class="hover:text-yellow-300">About</RouterLink></li>
      <li><RouterLink to="/services" class="hover:text-yellow-300">Services</RouterLink></li>

      <!-- Gallery Dropdown -->
      <li class="relative group">
        <a href="/gallery" class="hover:text-yellow-300">Gallery <span>▾</span></a>
        <ul class="absolute left-0 mt-2 w-40 bg-green-800 text-white rounded-md shadow-lg opacity-0 group-hover:opacity-100 transition-opacity z-50">
          <li><RouterLink to="/gallery/images" class="block px-4 py-2 hover:bg-green-700">Images</RouterLink></li>
          <li><RouterLink to="/gallery/videos" class="block px-4 py-2 hover:bg-green-700">Videos</RouterLink></li>
        </ul>
      </li>

      <!-- Destination Dropdown -->
      <li class="relative group">
        <a href="/destination" class="hover:text-yellow-300">Destination <span>▾</span></a>
        <ul class="absolute left-0 mt-2 w-40 bg-green-800 text-white rounded-md shadow-lg opacity-0 group-hover:opacity-100 transition-opacity z-50">
          <li><RouterLink to="/kigali" class="block px-4 py-2 hover:bg-green-700">Kigali</RouterLink></li>
          <li><RouterLink to="/south" class="block px-4 py-2 hover:bg-green-700">South</RouterLink></li>
          <li><RouterLink to="/west" class="block px-4 py-2 hover:bg-green-700">West</RouterLink></li>
          <li><RouterLink to="/north" class="block px-4 py-2 hover:bg-green-700">North</RouterLink></li>
          <li><RouterLink to="/east" class="block px-4 py-2 hover:bg-green-700">East</RouterLink></li>
        </ul>
      </li>

      <li><RouterLink to="/contact" class="hover:text-yellow-300">Contact</RouterLink></li>

      <!-- Language Switcher -->
      <li class="relative group">
        <button class="flex items-center gap-1 border border-white/40 hover:border-yellow-300 hover:text-yellow-300 px-3 py-1 rounded-full transition text-sm">
          🌐 {{ currentLang.label }} <span>▾</span>
        </button>
        <ul class="absolute right-0 mt-2 w-40 bg-green-800 rounded-md shadow-lg opacity-0 group-hover:opacity-100 transition-opacity z-50">
          <li
            v-for="lang in languages"
            :key="lang.code"
            @click="setLang(lang)"
            class="flex items-center justify-between px-4 py-2 hover:bg-green-700 cursor-pointer"
            :class="currentLang.code === lang.code ? 'text-yellow-300' : 'text-white'"
          >
            <span>{{ lang.full }}</span>
            <span v-if="currentLang.code === lang.code" class="text-yellow-300 text-xs">✓</span>
          </li>
        </ul>
      </li>

    </ul>
  </nav>
</template>