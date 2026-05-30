<!-- src/components/home/FeaturesSection.vue -->
<template>
  <section class="relative py-24 px-[5%] max-w-7xl mx-auto overflow-x-hidden">
    <div class="text-center mb-8">
      <p class="text-[#bbf706] font-semibold uppercase tracking-widest text-sm mb-4">WHY GYMBOSS</p>
      <h2 class="text-4xl md:text-6xl font-extrabold leading-tight text-white">
        More Than a Gym.<br class="md:hidden" /> <span class="text-[#bbf706]">It's a Transformation Engine</span>
      </h2>
      <p class="text-neutral-400 mt-6 max-w-3xl mx-auto text-lg">
        Every piece of equipment, every class, and every coach exists for one reason: to make you unstoppable.
      </p>
    </div>

    <div class="space-y-24 lg:space-y-40">
      <div
        v-for="(item, idx) in features"
        :key="idx"
        ref="featureRows"
        class="grid lg:grid-cols-2 gap-12 lg:gap-20 items-center"
      >
        <div class="overflow-hidden rounded-2xl lg:order-1" :class="idx % 2 === 0 ? 'lg:order-2' : 'lg:order-1'">
          <img
            :src="item.image"
            :alt="item.label"
            class="w-full h-80 md:h-112.5 object-cover rounded-2xl hover:scale-105 transition-transform duration-700"
          />
        </div>
        <div class="space-y-6" :class="idx % 2 === 0 ? 'lg:order-1' : 'lg:order-2'">
          <span class="inline-block px-5 py-3 mb-4 bg-[#bbf706]/10 text-[#bbf706] text-xs font-bold uppercase tracking-wider rounded-full border border-[#bbf706]/30">
            {{ item.label }}
          </span>
          <h3 class="text-3xl lg:text-5xl font-extrabold text-white leading-tight">{{ item.title }}</h3>
          <p class="text-neutral-300 text-lg leading-relaxed">{{ item.description }}</p>
          <ul class="space-y-4">
            <li v-for="(point, i) in item.points" :key="i" class="flex items-start gap-4 group">
              <div class="w-8 h-8 bg-[#bbf706]/10 rounded-lg flex items-center justify-center shrink-0 mt-0.5 group-hover:bg-[#bbf706]/20 transition-colors">
                <CheckIcon class="w-5 h-5 text-[#bbf706]" />
              </div>
              <span class="text-neutral-200 text-base leading-relaxed">{{ point }}</span>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import { CheckIcon } from '@heroicons/vue/24/solid'

const features = [
  {
    label: 'CrossFit Group Classes',
    title: 'Sweat Together, Grow Together',
    description: 'Our group classes aren\'t just workouts - they\'re daily parties of sweat, music, and breakthroughs. Expect to laugh, suffer, and leave stronger than ever.',
    points: [
      '30-minute sessions designed for maximum results in minimum time',
      'Coaches who remember your name and push your limits',
      'A tribe that celebrates your wins - no matter how small'
    ],
    image: 'https://images.unsplash.com/photo-1517836357463-d25dfeac3438?q=80&w=1470&auto=format&fit=crop'
  },
  {
    label: 'Strength Training',
    title: 'Lift Heavy, Feel Invincible',
    description: 'Nothing builds confidence like pulling a deadlift you thought impossible. Our open-air strength zone is your temple of iron, ready for your next PR.',
    points: [
      'Eleiko bars, competition plates, and 8 dedicated platforms',
      'Atlas stones, yokes, and all the strongman toys',
      'Space to grunt, drop weights, and unleash your inner beast'
    ],
    image: 'https://images.unsplash.com/photo-1534438327276-14e5300c3a48?q=80&w=1470&auto=format&fit=crop'
  },
  {
    label: 'Personal Training',
    title: 'Your Success Has a Blueprint Now',
    description: 'Stop guessing and start getting results. Our coaches build you a step-by-step roadmap, hold you accountable, and celebrate every milestone with you.',
    points: [
      'Free body composition scan & goal-setting session',
      'Weekly check-ins to keep you on track',
      'Nutrition playbooks that actually taste good'
    ],
    image: 'https://images.unsplash.com/photo-1571019614242-c5c5dee9f50b?q=80&w=1470&auto=format&fit=crop'
  },
  {
    label: 'Member Events',
    title: 'Your Second Home, Not Just a Gym',
    description: 'From BBQ nights to friendly throwdowns, our events turn strangers into training partners and training partners into family.',
    points: [
      'Monthly "Friday Night Lights" fitness competitions',
      'Holiday parties & outdoor movie nights',
      'Exclusive seminars with pro athletes & coaches'
    ],
    image: 'https://images.unsplash.com/photo-1526506118025-a1c0d4a991f8?q=80&w=1470&auto=format&fit=crop'
  }
]

const featureRows = ref<HTMLElement[]>([])

onMounted(() => {
  if (featureRows.value.length) {
    gsap.from(featureRows.value, {
      opacity: 0,
      y: 60,
      duration: 0.8,
      stagger: 0.2,
      ease: 'power3.out',
      scrollTrigger: {
        trigger: featureRows.value[0],
        start: 'top 85%'
      }
    })
  }
})
</script>