<template>
  <section
    ref="heroWrapper"
    class="relative w-full h-[calc(100vh-var(--header-height,125px))] overflow-hidden select-none cursor-grab"
    :class="{ 'cursor-grabbing': isDragging }"
    @mousedown="onDragStart"
    @mousemove="onDragMove"
    @mouseup="onDragEnd"
    @mouseleave="onDragEnd"
    @touchstart.passive="onTouchStart"
    @touchmove="onTouchMove"
    @touchend="onDragEnd"
  >
    <div
      v-for="(slide, index) in slides"
      :key="index"
      class="absolute inset-0 w-full h-full flex flex-col justify-center items-center text-center px-5 transition-opacity duration-1000"
      :class="{ 'opacity-100 z-10': index === currentSlide, 'opacity-0 z-0': index !== currentSlide }"
    >
      <div
        class="absolute inset-0 z-0 bg-cover bg-center"
        :style="{ backgroundImage: `url(${slide.bg})` }"
      ></div>
      <div class="absolute inset-0 z-1" style="background: linear-gradient(rgba(10,10,10,0.6), rgba(10,10,10,0.9));"></div>
      <h1 class="relative z-2 text-4xl md:text-7xl font-extrabold leading-[1.05] tracking-tight max-w-3xl mb-6 text-white" :ref="el => handleTitleRef(el, index)">{{ slide.title }}</h1>
      <p class="relative z-2 text-base md:text-lg text-neutral-200 max-w-xl mb-10" :ref="el => handleSubRef(el, index)">{{ slide.sub }}</p>
      <a :href="slide.ctaLink" class="relative z-2 bg-[#bbf706] text-black px-8 py-4 rounded-full text-sm md:text-base font-semibold hover:scale-105 transition-transform" :ref="el => handleBtnRef(el, index)">{{ slide.cta }}</a>
    </div>

    <button @click="prevSlide" class="absolute left-4 top-1/2 -translate-y-1/2 z-20 bg-black/50 hover:bg-black/80 text-white rounded-full p-3 backdrop-blur-sm transition-all cursor-pointer">
      <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-5 h-5 md:w-6 md:h-6">
        <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 19.5L8.25 12l7.5-7.5" />
      </svg>
    </button>
    <button @click="nextSlide" class="absolute right-4 top-1/2 -translate-y-1/2 z-20 bg-black/50 hover:bg-black/80 text-white rounded-full p-3 backdrop-blur-sm transition-all cursor-pointer">
      <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-5 h-5 md:w-6 md:h-6">
        <path stroke-linecap="round" stroke-linejoin="round" d="M8.25 4.5l7.5 7.5-7.5 7.5" />
      </svg>
    </button>

    <div class="absolute bottom-8 left-1/2 -translate-x-1/2 z-20 flex gap-3">
      <button
        v-for="(_, index) in slides"
        :key="index"
        @click="goToSlide(index)"
        class="w-2.5 h-2.5 md:w-3 md:h-3 rounded-full transition-all duration-300 cursor-pointer"
        :class="index === currentSlide ? 'bg-[#bbf706] scale-125' : 'bg-white/50 hover:bg-white/80'"
      ></button>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted, nextTick } from 'vue'
import { gsap } from 'gsap'

const slides = [
  {
    bg: '/hero/image_1.jpg',
    title: 'Crush your health and fitness goals in no time',
    sub: 'It doesn\'t matter if your goal is to get stronger, burn fat, or to just stay fit our world class coaches will guide you every step of the way.',
    cta: 'Ready To Fight',
    ctaLink: '/#pricing'
  },
  {
    bg: '/hero/image_3.jpg',
    title: 'Transform your body, unleash your strength',
    sub: 'Join our community and experience the power of functional fitness in a supportive and energetic environment.',
    cta: 'Book your first class',
    ctaLink: '/contact'
  },
  {
    bg: '/hero/image_2.jpg',
    title: 'Where champions are made',
    sub: 'From beginners to elite athletes, our gym is designed to push your limits and redefine your potential.',
    cta: 'Start your journey',
    ctaLink: '/#pricing'
  }
]

const currentSlide = ref(0)
const slideTitles = ref<(HTMLElement | null)[]>([])
const slideSubs = ref<(HTMLElement | null)[]>([])
const slideBtns = ref<(HTMLElement | null)[]>([])

const isDragging = ref(false)
let dragStartX = 0
let dragCurrentX = 0
const dragThreshold = 50

let autoplayInterval: ReturnType<typeof setInterval> | null = null

const handleTitleRef = (el: unknown, index: number) => { slideTitles.value[index] = el instanceof HTMLElement ? el : null }
const handleSubRef = (el: unknown, index: number) => { slideSubs.value[index] = el instanceof HTMLElement ? el : null }
const handleBtnRef = (el: unknown, index: number) => { slideBtns.value[index] = el instanceof HTMLElement ? el : null }

const animateTextIn = (index: number) => {
  nextTick(() => {
    const title = slideTitles.value[index]
    const sub = slideSubs.value[index]
    const btn = slideBtns.value[index]
    if (title && sub && btn) {
      gsap.fromTo(title, { opacity: 0, y: 50, filter: 'blur(6px)' }, { opacity: 1, y: 0, filter: 'blur(0px)', duration: 0.8, ease: 'power2.out' })
      gsap.fromTo(sub, { opacity: 0, y: 30, filter: 'blur(4px)' }, { opacity: 1, y: 0, filter: 'blur(0px)', duration: 0.8, ease: 'power2.out', delay: 0.15 })
      gsap.fromTo(btn, { opacity: 0, y: 20, scale: 0.9 }, { opacity: 1, y: 0, scale: 1, duration: 0.6, ease: 'power2.out', delay: 0.3 })
    }
  })
}

const stopAutoplay = () => { if (autoplayInterval) { clearInterval(autoplayInterval); autoplayInterval = null } }
const startAutoplay = () => { stopAutoplay(); autoplayInterval = setInterval(() => { nextSlide() }, 6000) }

const nextSlide = () => { const next = (currentSlide.value + 1) % slides.length; goToSlide(next) }
const prevSlide = () => { const prev = (currentSlide.value - 1 + slides.length) % slides.length; goToSlide(prev) }

const goToSlide = (index: number) => {
  if (index === currentSlide.value) return
  currentSlide.value = index
  animateTextIn(index)
  startAutoplay()
}

const onDragStart = (e: MouseEvent) => {
  isDragging.value = true
  dragStartX = e.clientX
  dragCurrentX = e.clientX
  stopAutoplay()
}

const onDragMove = (e: MouseEvent) => {
  if (!isDragging.value) return
  dragCurrentX = e.clientX
}

const onDragEnd = () => {
  if (!isDragging.value) return
  isDragging.value = false
  const dx = dragStartX - dragCurrentX
  if (Math.abs(dx) > dragThreshold) {
    if (dx > 0) { nextSlide() } else { prevSlide() }
  }
  startAutoplay()
}

const onTouchStart = (e: TouchEvent) => {
  isDragging.value = true
  const touch = e.touches?.[0]
  if (touch) {
    dragStartX = touch.clientX
    dragCurrentX = touch.clientX
    stopAutoplay()
  }
}

const onTouchMove = (e: TouchEvent) => {
  if (!isDragging.value) return
  const touch = e.touches?.[0]
  if (touch) {
    dragCurrentX = touch.clientX
  }
}

onMounted(() => {
  animateTextIn(0)
  startAutoplay()
})

onUnmounted(() => {
  stopAutoplay()
})
</script>