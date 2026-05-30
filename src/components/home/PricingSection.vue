<template>
  <section id="pricing" class="py-24 px-[5%] max-w-7xl mx-auto">
    <div class="text-center mb-16">
      <p class="text-[#bbf706] font-semibold uppercase tracking-wider text-sm mb-4">Membership Plans</p>
      <h2 class="text-4xl md:text-5xl font-extrabold tracking-tight text-white">Choose your path to greatness</h2>
      <p class="text-neutral-400 mt-4 max-w-2xl mx-auto">Flexible plans designed to fit your lifestyle. Start your journey today.</p>
    </div>
    <div ref="pricingGrid" class="grid sm:grid-cols-2 lg:grid-cols-4 gap-6">
      <div class="bg-neutral-900 border border-neutral-800 rounded-2xl p-8 flex flex-col items-center text-center pricing-card">
        <span class="text-sm text-neutral-400 uppercase tracking-wider mb-2">Daily Pass</span>
        <div class="text-5xl font-extrabold text-white mt-4">Rp12k</div>
        <p class="text-neutral-500 text-sm mt-2">/ day</p>
        <a href="/contact" class="mt-8 w-full bg-[#bbf706] text-black py-3 rounded-full font-semibold hover:scale-105 transition-transform">Go to gym</a>
      </div>
      <div class="bg-neutral-900 border border-neutral-800 rounded-2xl p-8 flex flex-col items-center text-center pricing-card">
        <span class="text-sm text-neutral-400 uppercase tracking-wider mb-2">1 Month</span>
        <div class="text-5xl font-extrabold text-white mt-4">Rp120k</div>
        <p class="text-neutral-500 text-sm mt-2">/ month</p>
        <a href="/contact" class="mt-8 w-full bg-[#bbf706] text-black py-3 rounded-full font-semibold hover:scale-105 transition-transform">Get started</a>
      </div>
      <div class="bg-neutral-900 border border-neutral-800 rounded-2xl p-8 flex flex-col items-center text-center pricing-card">
        <span class="text-sm text-neutral-400 uppercase tracking-wider mb-2">3 Months</span>
        <div class="text-5xl font-extrabold text-white mt-4">Rp340k</div>
        <p class="text-neutral-500 text-sm mt-2">/ 3 months</p>
        <a href="/contact" class="mt-8 w-full bg-[#bbf706] text-black py-3 rounded-full font-semibold hover:scale-105 transition-transform">Join now</a>
      </div>
      <div class="bg-neutral-900 border border-neutral-800 rounded-2xl p-8 flex flex-col items-center text-center pricing-card">
        <span class="text-sm text-neutral-400 uppercase tracking-wider mb-2">6 Months</span>
        <div class="text-5xl font-extrabold text-white mt-4">Rp620k</div>
        <p class="text-neutral-500 text-sm mt-2">/ 6 months</p>
        <a href="/contact" class="mt-8 w-full bg-[#bbf706] text-black py-3 rounded-full font-semibold hover:scale-105 transition-transform">I am a fighter</a>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

const pricingGrid = ref<HTMLElement | null>(null)

onMounted(() => {
  const cards = document.querySelectorAll('.pricing-card')
  gsap.from(cards, {
    opacity: 0,
    y: 60,
    stagger: 0.15,
    duration: 0.8,
    ease: 'power2.out',
    scrollTrigger: {
      trigger: '#pricing',
      start: 'top 80%'
    }
  })
})
</script>