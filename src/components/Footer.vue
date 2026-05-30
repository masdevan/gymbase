<template>
  <footer class="border-t border-neutral-800 py-12 px-[5%] flex flex-col md:flex-row justify-between items-center gap-6">
    <router-link to="/" class="flex items-center gap-2 text-lg font-bold">
      <img src="/core/logo.png" alt="Gymbase" class="w-6 h-6" />
      <span>Gymbase</span>
    </router-link>
    <div class="flex flex-wrap justify-center gap-6 text-neutral-400 text-sm">
      <router-link to="/" class="hover:text-white transition-colors">Home</router-link>
      <router-link to="/services" class="hover:text-white transition-colors">CrossFit Classes</router-link>
      <router-link to="/services" class="hover:text-white transition-colors">Strength Training</router-link>
      <router-link to="/services" class="hover:text-white transition-colors">Personal Training</router-link>
      <router-link to="/services" class="hover:text-white transition-colors">Member Events</router-link>
      <router-link to="/about" class="hover:text-white transition-colors">About</router-link>
      <router-link to="/contact" class="hover:text-white transition-colors">Contact</router-link>
    </div>
    <p class="text-neutral-500 text-sm">Copyright 2022 | Gymbase</p>
  </footer>
</template>

<script setup lang="ts">
import { onMounted } from 'vue'
import { gsap } from 'gsap'

onMounted(() => {
  gsap.from('footer', { opacity: 0, y: 30, duration: 0.8, ease: 'power2.out', scrollTrigger: { trigger: 'footer', start: 'top 90%' } })
})
</script>