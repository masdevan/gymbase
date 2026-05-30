<template>
  <div>
    <section class="relative h-[50vh] min-h-100 flex items-center justify-center overflow-hidden">
      <div class="absolute inset-0 z-0">
        <div class="absolute inset-0 bg-cover bg-center scale-110" style="background-image: url('/hero/image_1.jpg')"></div>
        <div class="absolute inset-0 bg-linear-to-b from-black/80 via-black/60 to-black/90"></div>
      </div>
      <div class="relative z-10 text-center px-4 max-w-4xl mx-auto">
        <h1 class="text-4xl sm:text-5xl md:text-7xl font-extrabold text-white mb-4 tracking-tight">Our <span class="text-[#bbf706]">Services</span></h1>
        <p class="text-base sm:text-lg md:text-xl text-neutral-300 max-w-2xl mx-auto">Elite training. Premium facilities. Unmatched community.</p>
      </div>
    </section>

    <section class="py-24 px-4 sm:px-6 md:px-[5%] max-w-7xl mx-auto">
      <div class="text-center mb-16">
        <span class="text-[#bbf706] font-bold uppercase tracking-wider text-sm">What we offer</span>
        <h2 class="text-3xl sm:text-4xl md:text-5xl font-extrabold text-white mt-2">Everything you need to dominate</h2>
        <div class="w-20 h-1 bg-[#bbf706] mx-auto mt-4"></div>
      </div>

      <div class="grid md:grid-cols-2 gap-8 lg:gap-10">
        <div
          v-for="(service, index) in services"
          :key="index"
          ref="cardRefs"
          class="service-card relative bg-linear-to-br from-neutral-900 to-neutral-950 rounded-2xl overflow-hidden border border-neutral-800 transition-all duration-300 cursor-pointer"
        >
          <div
            class="glow-spot absolute rounded-full pointer-events-none opacity-0 transition-opacity duration-200"
            style="width: 280px; height: 280px; background: radial-gradient(circle, rgba(187,247,6,0.2) 0%, rgba(187,247,6,0) 70%); transform: translate(-50%, -50%);"
          ></div>
          <div class="p-6 sm:p-8 relative z-10">
            <div class="w-14 h-14 rounded-xl bg-[#bbf706]/10 flex items-center justify-center mb-6 border border-[#bbf706]/20">
              <component :is="service.icon" class="w-7 h-7 text-[#bbf706]" />
            </div>
            <h3 class="text-2xl font-bold text-white mb-3">{{ service.title }}</h3>
            <p class="text-neutral-400 mb-4 leading-relaxed">{{ service.description }}</p>
            <ul class="space-y-2">
              <li v-for="(feature, idx) in service.features" :key="idx" class="flex items-center gap-2 text-sm text-neutral-500">
                <CheckIcon class="w-4 h-4 text-[#bbf706]" />
                <span>{{ feature }}</span>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <section class="py-20 bg-neutral-900/50 relative overflow-hidden">
      <div class="absolute inset-0 opacity-10 bg-[url('/hero/image_2.jpg')] bg-cover bg-center"></div>
      <div class="relative z-10 px-4 sm:px-6 md:px-[5%] max-w-7xl mx-auto text-center">
        <h2 class="text-3xl sm:text-4xl md:text-5xl font-extrabold text-white mb-4">Ready to start?</h2>
        <p class="text-neutral-400 max-w-2xl mx-auto mb-8">Book your first session today and experience the Gymbase difference.</p>
        <router-link to="/contact" class="inline-block bg-[#bbf706] text-black px-8 py-3 rounded-full font-semibold hover:scale-105 transition-transform">Get in touch</router-link>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'
import { FireIcon, BoltIcon, UserGroupIcon, CalendarIcon, CheckIcon } from '@heroicons/vue/24/outline'

const services = [
  {
    icon: FireIcon,
    title: 'CrossFit Group Classes',
    description: 'High-intensity functional training in a group setting. 30-minute sessions include warm-up and workout.',
    features: ['Scalable for all levels', 'Expert coaching', 'Community driven']
  },
  {
    icon: BoltIcon,
    title: 'Strength Training',
    description: 'Access to powerlifting platforms, Olympic weights, dumbbells up to 250lbs, and strongman equipment.',
    features: ['Eleiko competition bars', 'Squat racks & deadlift platforms', 'Strongman equipment']
  },
  {
    icon: UserGroupIcon,
    title: 'Personal Training',
    description: 'One-on-one coaching for weight loss, competitive CrossFit, or powerlifting goals.',
    features: ['Customized programming', 'Nutrition guidance', 'Weekly progress tracking']
  },
  {
    icon: CalendarIcon,
    title: 'Member Events',
    description: 'Monthly challenges, friendly competitions, and summer potlucks to build community.',
    features: ['Friday Night Lights', 'Seasonal socials', 'Exclusive seminars']
  }
]

const cardRefs = ref<(HTMLElement | null)[]>([])
const cleanupFns: (() => void)[] = []

onMounted(() => {
  cardRefs.value.forEach((card) => {
    if (!card) return
    const glow = card.querySelector('.glow-spot') as HTMLElement
    if (!glow) return

    const onMouseMove = (e: MouseEvent) => {
      const rect = card.getBoundingClientRect()
      const x = e.clientX - rect.left
      const y = e.clientY - rect.top
      glow.style.left = `${x}px`
      glow.style.top = `${y}px`
      glow.style.opacity = '1'
    }
    const onMouseLeave = () => {
      glow.style.opacity = '0'
    }
    card.addEventListener('mousemove', onMouseMove)
    card.addEventListener('mouseleave', onMouseLeave)
    cleanupFns.push(() => {
      card.removeEventListener('mousemove', onMouseMove)
      card.removeEventListener('mouseleave', onMouseLeave)
    })
  })
})

onUnmounted(() => {
  cleanupFns.forEach(fn => fn())
})
</script>

<style scoped>
.service-card {
  cursor: pointer;
}
.glow-spot {
  will-change: left, top, opacity;
  pointer-events: none;
  z-index: 5;
}
.service-card .glow-spot {
  transition: opacity 0.2s ease;
}
</style>