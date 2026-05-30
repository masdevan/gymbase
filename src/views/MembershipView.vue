<template>
  <div>
    <section class="relative h-[50vh] min-h-100 flex items-center justify-center overflow-hidden">
      <div class="absolute inset-0 z-0">
        <div class="absolute inset-0 bg-cover bg-center scale-110" style="background-image: url('/hero/image_1.jpg')"></div>
        <div class="absolute inset-0 bg-linear-to-b from-black/80 via-black/60 to-black/90"></div>
      </div>
      <div class="relative z-10 text-center px-4 max-w-4xl mx-auto">
        <h1 class="text-5xl md:text-7xl font-extrabold text-white mb-4 tracking-tight">Membership <span class="text-[#bbf706]">Plans</span></h1>
        <p class="text-lg md:text-xl text-neutral-300 max-w-2xl mx-auto">Choose the plan that fits your goals. No hidden fees, no contracts just results.</p>
      </div>
    </section>

    <section id="pricing" class="py-24 px-4 sm:px-6 md:px-[5%] max-w-7xl mx-auto">
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

    <section class="py-20 bg-neutral-900/50">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 md:px-[5%]">
        <div class="grid md:grid-cols-2 gap-12 items-center">
          <div>
            <span class="text-[#bbf706] font-bold uppercase tracking-wider text-sm">Included with all plans</span>
            <h2 class="text-3xl md:text-4xl font-extrabold text-white mt-2">Everything you need to succeed</h2>
            <ul class="space-y-4 mt-8">
              <li v-for="benefit in benefits" :key="benefit" class="flex items-start gap-3">
                <div class="w-6 h-6 rounded-full bg-[#bbf706]/20 flex items-center justify-center mt-0.5">
                  <CheckIcon class="w-3 h-3 text-[#bbf706]" />
                </div>
                <span class="text-neutral-300">{{ benefit }}</span>
              </li>
            </ul>
          </div>
          <div class="relative rounded-2xl overflow-hidden">
            <img src="/main/image_1.jpg" alt="Gym facilities" class="w-full h-auto object-cover rounded-2xl border border-neutral-800">
            <div class="absolute inset-0 bg-linear-to-t from-black/60 to-transparent rounded-2xl"></div>
          </div>
        </div>
      </div>
    </section>

    <section class="py-20 px-4 sm:px-6 md:px-[5%] max-w-7xl mx-auto text-center">
      <h2 class="text-3xl md:text-5xl font-extrabold text-white mb-4">Not sure which plan is right for you?</h2>
      <p class="text-neutral-400 max-w-2xl mx-auto mb-8">Book a free tour and consultation. We'll help you find your perfect fit.</p>
      <router-link to="/contact" class="inline-flex items-center gap-2 bg-[#bbf706] text-black px-8 py-3 rounded-full font-semibold hover:scale-105 transition-transform">
        Book a free tour
        <ArrowRightIcon class="w-4 h-4" />
      </router-link>
    </section>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import { CheckIcon, ArrowRightIcon } from '@heroicons/vue/24/outline'

const pricingGrid = ref<HTMLElement | null>(null)

const benefits = [
  'State-of-the-art equipment and facility',
  'Unlimited CrossFit and strength classes',
  'Access to locker rooms with showers',
  'Free parking and bike storage',
  'Discounts on merchandise and events',
  'Community challenges and social events'
]

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