<template>
  <div>
    <section class="relative h-[calc(100vh-125px)] flex items-center justify-center overflow-hidden">
      <div class="absolute inset-0 z-0">
        <div class="absolute inset-0 bg-cover bg-center scale-110" style="background-image: url('/about_background/image_3.jpg')"></div>
        <div class="absolute inset-0 bg-linear-to-b from-black/70 via-black/50 to-black/90"></div>
      </div>
      <div class="relative z-10 text-center px-4 max-w-4xl mx-auto">
        <h1 class="hero-title text-6xl md:text-8xl font-extrabold text-white mb-6 tracking-tight">FORGE YOUR <span class="text-[#bbf706]">LEGACY</span></h1>
        <p class="hero-sub text-xl md:text-2xl text-neutral-200 max-w-2xl mx-auto">More than a gym. A brotherhood of iron, sweat, and unbreakable spirit.</p>
      </div>
      <div class="absolute bottom-10 left-1/2 transform -translate-x-1/2 animate-bounce">
        <ArrowDownIcon class="w-6 h-6 text-white" />
      </div>
    </section>

    <section class="py-24 px-[5%] max-w-7xl mx-auto">
      <div class="grid md:grid-cols-2 gap-16 items-center">
        <div class="story-text space-y-6">
          <span class="text-[#bbf706] font-bold uppercase tracking-wider text-sm">Our story</span>
          <h2 class="text-4xl md:text-5xl font-extrabold text-white leading-tight">Born in the trenches of Boyolali</h2>
          <p class="text-neutral-300 text-lg">What started as a garage gym with two mismatched barbells and a dream has exploded into the most feared and respected fitness tribe in Central Java. Alex & Sparky built this place for the underdogs, the grinders, the ones who refuse to settle.</p>
          <p class="text-neutral-400">We don't do mediocrity. We don't do excuses. You walk through our doors, you become family. And family pushes each other to the breaking point – then picks them back up.</p>
          <div class="pt-4 flex gap-8 stats-container">
            <div><div class="text-4xl font-black text-[#bbf706] stat-number">12+</div><div class="text-neutral-500">Years of Pain</div></div>
            <div><div class="text-4xl font-black text-[#bbf706] stat-number">500+</div><div class="text-neutral-500">Warriors forged</div></div>
            <div><div class="text-4xl font-black text-[#bbf706] stat-number">10k+</div><div class="text-neutral-500">Tons lifted</div></div>
          </div>
        </div>
        <div class="story-image relative rounded-2xl overflow-hidden shadow-2xl group">
          <img src="/about_background/image_2.jpg" alt="Gymbase history" class="w-full h-auto object-cover transition-transform duration-700 group-hover:scale-105">
          <div class="absolute inset-0 bg-linear-to-t from-black/60 to-transparent"></div>
        </div>
      </div>
    </section>

    <section class="py-24 bg-neutral-900/50 relative overflow-hidden">
      <div class="absolute inset-0 opacity-10 bg-[url('/about_background/image_1.jpg')] bg-cover bg-center"></div>
      <div class="relative z-10 px-[5%] max-w-7xl mx-auto text-center">
        <span class="values-label text-[#bbf706] font-bold uppercase tracking-wider text-sm">What we stand for</span>
        <h2 class="values-head text-4xl md:text-6xl font-extrabold text-white mt-4 mb-16">The Gymbase Code</h2>
        <div class="grid md:grid-cols-3 gap-8">
          <div v-for="(value, i) in values" :key="i" class="bg-neutral-800/50 backdrop-blur-sm border border-neutral-700 rounded-2xl p-8 text-center hover:border-[#bbf706] transition-all duration-300 hover:-translate-y-2">
            <component :is="value.icon" class="w-12 h-12 text-[#bbf706] mx-auto mb-4" />
            <h3 class="text-2xl font-bold text-white mb-3">{{ value.title }}</h3>
            <p class="text-neutral-400">{{ value.desc }}</p>
          </div>
        </div>
      </div>
    </section>

    <section class="py-24 px-[5%] max-w-7xl mx-auto">
      <div class="text-center mb-16">
        <span class="coach-label text-[#bbf706] font-bold uppercase tracking-wider text-sm">The architects of pain</span>
        <h2 class="text-4xl md:text-6xl font-extrabold text-white mt-2">Meet your coaches</h2>
        <p class="text-neutral-400 max-w-2xl mx-auto mt-4">World-class experts who've walked the walk. They'll break you down to build you stronger.</p>
      </div>
      
      <div class="flex flex-col gap-20">
        <div v-for="(coach, idx) in coaches" :key="idx" class="coach-row flex flex-col md:flex-row items-center gap-8 md:gap-12 even:md:flex-row-reverse group">
          <div class="coach-photo w-full md:w-1/3 relative">
            <div class="relative rounded-3xl overflow-hidden shadow-2xl transition-transform duration-500 group-hover:scale-105">
              <img :src="coach.img" :alt="coach.name" class="w-full h-80 md:h-96 object-cover">
              <div class="absolute inset-0 bg-linear-to-t from-black/80 via-black/20 to-transparent"></div>
            </div>
          </div>
          <div class="coach-info w-full md:w-2/3 space-y-4">
            <h3 class="text-3xl md:text-5xl font-black text-white tracking-tight">{{ coach.name }}</h3>
            <div class="flex items-center gap-3">
              <p class="text-[#bbf706] font-bold text-lg uppercase tracking-wider">{{ coach.role }}</p>
            </div>
            <p class="text-neutral-300 text-lg leading-relaxed">{{ coach.bio }}</p>
          </div>
        </div>
      </div>
    </section>

    <section class="relative py-32 overflow-hidden">
      <div class="absolute inset-0 bg-[url('/about_background/image_4.jpg')] bg-cover bg-center">
        <div class="absolute inset-0 bg-black/70"></div>
      </div>
      <div class="relative z-10 text-center px-4">
        <h2 class="text-4xl md:text-7xl font-extrabold text-white mb-6">Ready to join the pack?</h2>
        <p class="text-xl text-neutral-200 max-w-2xl mx-auto mb-10">Your first session is on us. No strings, just sweat.</p>
        <router-link to="/contact" class="inline-block bg-[#bbf706] text-black px-10 py-4 rounded-full text-lg font-bold hover:scale-105 transition-transform">Yes I'm Ready</router-link>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
import { onMounted } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import { ArrowDownIcon, ShieldCheckIcon, FireIcon, UsersIcon } from '@heroicons/vue/24/solid'

const values = [
  { icon: ShieldCheckIcon, title: 'No ego', desc: 'Leave your pride at the door. We grow together.' },
  { icon: FireIcon, title: 'Embrace the suck', desc: 'Growth lives in discomfort. Get comfortable being uncomfortable.' },
  { icon: UsersIcon, title: 'Family first', desc: 'We celebrate PRs, mourn losses, and always show up.' }
]

const coaches = [
  { name: 'Heru Firmansyah', role: 'Head Coach & Founder', bio: '12 years CrossFit experience. Regional competitor. His hype is contagious. He will push you beyond your limits and celebrate every PR like it\'s his own.', img: '/about_coach/image_1.jpg' },
  { name: 'Fendi Nurahman', role: 'Strength & Conditioning', bio: 'Former powerlifter with a 600lb deadlift. Technique freak who breaks down every movement to perfection. Your squat will never be the same.', img: '/about_coach/image_2.jpg' },
  { name: 'Valentina Taulany', role: 'Mobility & Recovery', bio: 'Yoga master & rehab specialist. She’ll fix your broken parts and teach you that flexibility is the secret weapon of every champion.', img: '/about_coach/image_3.jpg' },
  { name: 'Raska Tomi', role: 'Olympic Lifting', bio: 'Weightlifting coach, snatch specialist. Precision over ego. He\'ll transform your power into poetry. Clean & jerk will become your favorite movement.', img: '/about_coach/image_4.jpg' }
]

onMounted(() => {
  ScrollTrigger.refresh()

  gsap.from('.hero-title', { opacity: 0, y: 80, duration: 1, ease: 'power3.out' })
  gsap.from('.hero-sub', { opacity: 0, y: 40, duration: 0.8, delay: 0.3 })

  gsap.from('.story-text', {
    scrollTrigger: { trigger: '.story-text', start: 'top 85%' },
    opacity: 0, x: -60, duration: 0.8
  })
  gsap.from('.story-image', {
    scrollTrigger: { trigger: '.story-image', start: 'top 85%' },
    opacity: 0, x: 60, duration: 0.8
  })
  gsap.from('.stat-number', {
    scrollTrigger: { trigger: '.stats-container', start: 'top 90%' },
    opacity: 0, y: 20, stagger: 0.1, duration: 0.5
  })

  gsap.from('.values-label', {
    scrollTrigger: { trigger: '.values-label', start: 'top 85%' },
    opacity: 0, y: 30, duration: 0.6
  })
  gsap.from('.values-head', {
    scrollTrigger: { trigger: '.values-head', start: 'top 85%' },
    opacity: 0, y: 30, duration: 0.6
  })

  gsap.from('.coach-label', {
    scrollTrigger: { trigger: '.coach-label', start: 'top 85%' },
    opacity: 0, y: 30, duration: 0.6
  })
  
  gsap.from('.coach-row', {
    scrollTrigger: { trigger: '.coach-row', start: 'top 85%' },
    opacity: 0, y: 60, stagger: 0.2, duration: 0.8
  })
})
</script>