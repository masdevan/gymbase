<template>
  <section class="py-24 px-[5%] max-w-4xl mx-auto">
    <p ref="aboutLabel" class="text-[#bbf706] font-semibold uppercase tracking-wider text-sm mb-4">About Gymbase</p>
    <h2 ref="aboutHeading" class="text-5xl font-extrabold leading-tight mb-8 text-white">Hi! We're a local CrossFit gym in Boyolali, Indonesia.</h2>
    <p ref="aboutP1" class="text-lg text-neutral-400 mb-6">Gymbase was started by Alex and Sparky in 2012. It's our mission to help people in Boyolali get fit, stay healthy, and live life on their terms without fitness being an obstacle.</p>
    <p ref="aboutP2" class="text-lg text-neutral-400">Our coaches are world-class and our community is like no other. We believe fitness should be accessible, fun, and empowering. Come see for yourself.</p>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { gsap } from 'gsap'

const aboutLabel = ref(null)
const aboutHeading = ref(null)
const aboutP1 = ref(null)
const aboutP2 = ref(null)

onMounted(() => {
  const tl = gsap.timeline({ defaults: { ease: 'power2.out', duration: 0.8 } })
  tl.from(aboutLabel.value, { opacity: 0, y: 20 })
  tl.from(aboutHeading.value, { opacity: 0, y: 30 }, '-=0.3')
  tl.from(aboutP1.value, { opacity: 0, y: 20 }, '-=0.2')
  tl.from(aboutP2.value, { opacity: 0, y: 20 }, '-=0.1')
})
</script>