<template>
  <section ref="multiFooter" class="relative bg-neutral-950 py-20 px-[5%] border-t-2 border-[#bbf706] overflow-hidden">
    <div class="absolute inset-0 opacity-10 pointer-events-none" style="background-image: url('/core/pattern.png'); background-repeat: repeat; background-position: center; background-size: 180px;"></div>
    <div class="relative z-10 max-w-8xl mx-auto grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-12">
      <div>
        <router-link to="/" class="flex items-center gap-2 text-2xl font-extrabold mb-4">
          <img src="/core/logo.png" alt="Gymbase" class="w-7 h-7" />
          <span class="text-white">Gymbase</span>
        </router-link>
        <p class="text-neutral-400 text-sm leading-relaxed max-w-xs">
          A local CrossFit gym in Boyolali, Indonesia. Helping you crush your health and fitness goals since 2012.
        </p>
      </div>
      <div>
        <h4 class="text-white font-semibold mb-4 text-sm uppercase tracking-wider">Quick Links</h4>
        <ul class="space-y-3 text-sm text-neutral-400">
          <li><router-link to="/contact" class="hover:text-[#bbf706] transition-colors">Contact</router-link></li>
          <li><router-link to="/about" class="hover:text-[#bbf706] transition-colors">About</router-link></li>
          <li><router-link to="/training" class="hover:text-[#bbf706] transition-colors">Training</router-link></li>
          <li><router-link to="/membership" class="hover:text-[#bbf706] transition-colors">Membership</router-link></li>
        </ul>
      </div>
      <div>
        <h4 class="text-white font-semibold mb-4 text-sm uppercase tracking-wider">Contact</h4>
        <ul class="space-y-4 text-sm text-neutral-400">
          <li class="flex items-start gap-3">
            <MapPinIcon class="w-5 h-5 text-[#bbf706] shrink-0 mt-0.5" />
            <span>Jl. Raya Boyolali No. 123, Boyolali, Indonesia</span>
          </li>
          <li class="flex items-center gap-3">
            <PhoneIcon class="w-5 h-5 text-[#bbf706] shrink-0" />
            <span>0877-1234-5678</span>
          </li>
          <li class="flex items-center gap-3">
            <EnvelopeIcon class="w-5 h-5 text-[#bbf706] shrink-0" />
            <span>info@gymbase.id</span>
          </li>
        </ul>
      </div>
      <div>
        <h4 class="text-white font-semibold mb-4 text-sm uppercase tracking-wider">Hours</h4>
        <ul class="space-y-2 text-sm text-neutral-400">
          <li class="flex justify-between"><span>Mon - Fri</span><span class="text-white font-medium">06:00 AM - 10:00 PM</span></li>
          <li class="flex justify-between"><span>Saturday</span><span class="text-white font-medium">06:00 AM - 08:00 PM</span></li>
          <li class="flex justify-between"><span>Sunday</span><span class="text-white font-medium">07:00 AM - 02:00 PM</span></li>
        </ul>
        <router-link to="/contact" class="inline-block mt-6 bg-[#bbf706] text-black px-6 py-3 rounded-full text-sm font-semibold hover:scale-105 transition-transform">
          Ready To Fight
        </router-link>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import { MapPinIcon, PhoneIcon, EnvelopeIcon, GlobeAltIcon, ChatBubbleLeftRightIcon, CameraIcon } from '@heroicons/vue/24/outline'

const multiFooter = ref<HTMLElement | null>(null)

onMounted(() => {
  if (multiFooter.value) {
    const cols = multiFooter.value.querySelectorAll('.grid > div')
    gsap.from(cols, {
      opacity: 0,
      y: 20,
      stagger: 0.08,
      duration: 0.6,
      ease: 'power2.out',
      scrollTrigger: {
        trigger: multiFooter.value,
        start: 'top 90%'
      }
    })
  }
})
</script>