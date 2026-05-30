<template>
  <section class="py-24 px-[5%] max-w-7xl mx-auto">
    <div class="text-center mb-16">
      <h2 class="text-4xl md:text-5xl font-extrabold tracking-tight text-white">Our Services</h2>
    </div>
    <div ref="servicesGrid" class="grid md:grid-cols-2 gap-12">
      <div class="bg-neutral-900 p-8 rounded-2xl border border-neutral-800 service-card">
        <h3 class="text-2xl font-bold mb-4 text-white">CrossFit Group Classes</h3>
        <p class="text-neutral-400">High-intensity functional training in a group setting. 30-minute sessions include warm-up and workout.</p>
      </div>
      <div class="bg-neutral-900 p-8 rounded-2xl border border-neutral-800 service-card">
        <h3 class="text-2xl font-bold mb-4 text-white">Strength Training</h3>
        <p class="text-neutral-400">Access to powerlifting platforms, Olympic weights, dumbbells up to 250lbs, and strongman equipment.</p>
      </div>
      <div class="bg-neutral-900 p-8 rounded-2xl border border-neutral-800 service-card">
        <h3 class="text-2xl font-bold mb-4 text-white">Personal Training</h3>
        <p class="text-neutral-400">One-on-one coaching for weight loss, competitive CrossFit, or powerlifting goals.</p>
      </div>
      <div class="bg-neutral-900 p-8 rounded-2xl border border-neutral-800 service-card">
        <h3 class="text-2xl font-bold mb-4 text-white">Member Events</h3>
        <p class="text-neutral-400">Monthly challenges, friendly competitions, and summer potlucks to build community.</p>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { gsap } from 'gsap'

const servicesGrid = ref(null)

onMounted(() => {
  const cards = document.querySelectorAll('.service-card')
  gsap.from(cards, {
    opacity: 0,
    y: 50,
    stagger: 0.15,
    duration: 0.7,
    ease: 'power3.out',
    scrollTrigger: {
      trigger: servicesGrid.value,
      start: 'top 85%'
    }
  })
})
</script>