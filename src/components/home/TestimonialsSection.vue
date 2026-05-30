<!-- src/components/home/TestimonialsSection.vue -->
<template>
  <section class="py-24 px-[5%] max-w-7xl mx-auto overflow-hidden">
    <div class="text-center mb-16">
      <h2 class="text-4xl md:text-5xl font-extrabold tracking-tight text-white">What Our Members Say</h2>
      <p class="text-neutral-400 mt-4 max-w-2xl mx-auto">
        Real transformations, honest stories. See why hundreds in Boyolali choose Gymbase to crush their fitness goals.
      </p>
    </div>

    <div class="hidden md:grid grid-cols-3 gap-6 h-175 overflow-hidden">
      <div
        class="overflow-hidden relative h-full"
        @mouseenter="pauseTween('left')"
        @mouseleave="resumeTween('left')"
      >
        <div ref="leftCol" class="flex flex-col gap-6 absolute w-full">
          <TestimonialCard v-for="(item, i) in leftColumn" :key="'L'+i" :item="item" />
          <TestimonialCard v-for="(item, i) in leftColumn" :key="'Ld'+i" :item="item" />
        </div>
      </div>
      <div
        class="overflow-hidden relative h-full"
        @mouseenter="pauseTween('center')"
        @mouseleave="resumeTween('center')"
      >
        <div ref="centerCol" class="flex flex-col gap-6 absolute w-full">
          <TestimonialCard v-for="(item, i) in centerColumn" :key="'C'+i" :item="item" />
          <TestimonialCard v-for="(item, i) in centerColumn" :key="'Cd'+i" :item="item" />
        </div>
      </div>
      <div
        class="overflow-hidden relative h-full"
        @mouseenter="pauseTween('right')"
        @mouseleave="resumeTween('right')"
      >
        <div ref="rightCol" class="flex flex-col gap-6 absolute w-full">
          <TestimonialCard v-for="(item, i) in rightColumn" :key="'R'+i" :item="item" />
          <TestimonialCard v-for="(item, i) in rightColumn" :key="'Rd'+i" :item="item" />
        </div>
      </div>
    </div>

    <div class="md:hidden flex flex-col gap-6">
      <div
        class="overflow-hidden px-1 py-2"
        @mouseenter="pauseMobile(1)"
        @mouseleave="resumeMobile(1)"
        @touchstart="pauseMobile(1)"
        @touchend="resumeMobile(1)"
      >
        <div ref="mobileRow1" class="flex gap-6 w-max">
          <div v-for="(item, i) in mobileRow1Data" :key="'R1-'+i" class="w-[85vw] max-w-sm shrink-0">
            <TestimonialCard :item="item" />
          </div>
          <div v-for="(item, i) in mobileRow1Data" :key="'R1d-'+i" class="w-[85vw] max-w-sm shrink-0">
            <TestimonialCard :item="item" />
          </div>
        </div>
      </div>
      <div
        class="overflow-hidden px-1 py-2"
        @mouseenter="pauseMobile(2)"
        @mouseleave="resumeMobile(2)"
        @touchstart="pauseMobile(2)"
        @touchend="resumeMobile(2)"
      >
        <div ref="mobileRow2" class="flex gap-6 w-max">
          <div v-for="(item, i) in mobileRow2Data" :key="'R2-'+i" class="w-[85vw] max-w-sm shrink-0">
            <TestimonialCard :item="item" />
          </div>
          <div v-for="(item, i) in mobileRow2Data" :key="'R2d-'+i" class="w-[85vw] max-w-sm shrink-0">
            <TestimonialCard :item="item" />
          </div>
        </div>
      </div>
      <div
        class="overflow-hidden px-1 py-2"
        @mouseenter="pauseMobile(3)"
        @mouseleave="resumeMobile(3)"
        @touchstart="pauseMobile(3)"
        @touchend="resumeMobile(3)"
      >
        <div ref="mobileRow3" class="flex gap-6 w-max">
          <div v-for="(item, i) in mobileRow3Data" :key="'R3-'+i" class="w-[85vw] max-w-sm shrink-0">
            <TestimonialCard :item="item" />
          </div>
          <div v-for="(item, i) in mobileRow3Data" :key="'R3d-'+i" class="w-[85vw] max-w-sm shrink-0">
            <TestimonialCard :item="item" />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { gsap } from 'gsap'
import TestimonialCard from './TestimonialCard.vue'

interface Testimonial {
  initials: string
  name: string
  location: string
  duration: string
  quote: string
}

const testimonials: Testimonial[] = [
  { initials: 'AD', name: 'Agus Darmawan', location: 'Boyolali', duration: '6 months', quote: 'Sakwise gabung 6 bulan, bobotku mudun 15kg lan aku dadi luwih kuat. Suasanane nyenengake!' },
  { initials: 'SW', name: 'Sarah Williams', location: 'Solo', duration: '4 months', quote: "I've gotten so much stronger after joining it's insane. My deadlift increased by 65lbs. The coaches are world class." },
  { initials: 'BK', name: 'Budi Kurniawan', location: 'Klaten', duration: '1 year', quote: 'Nggo aku Gymbase kuwi komunitas sing luar biasa. Latihan bareng konco-konco nggawe semangat tambah.' },
  { initials: 'MA', name: 'Mega Anggraini', location: 'Kartasura', duration: '3 months', quote: 'Pelatihnya sabar dan profesional. Sekarang aku lebih percaya diri dan badan lebih bugar.' },
  { initials: 'DR', name: 'David Rachman', location: 'Sukoharjo', duration: '8 months', quote: "While I am passionate about fitness, this gym is more like a family. Friendly competitions push me further." },
  { initials: 'NN', name: 'Nina Novitasari', location: 'Boyolali', duration: '5 months', quote: 'Latihan 30 menit setiap hari kerasa ringan tapi hasilnya mantap. Cocok banget buat ibu rumah tangga.' },
  { initials: 'RA', name: 'Rizky Ardian', location: 'Solo', duration: '2 months', quote: 'Awalnya ragu, tapi setelah coba free trial langsung ketagihan. Sekarang tiap hari pengen ke gym terus!' },
  { initials: 'LM', name: 'Lisa Marlina', location: 'Boyolali', duration: '1 year', quote: 'Dari yang nggak bisa push-up, sekarang bisa angkat beban 50kg. Gila sih progressnya!' },
  { initials: 'AP', name: 'Andi Prasetyo', location: 'Klaten', duration: '9 months', quote: 'Best decision ever. My blood pressure is normal now and I feel 10 years younger.' }
]

const leftColumn = testimonials.slice(0, 3)
const centerColumn = testimonials.slice(3, 6)
const rightColumn = testimonials.slice(6, 9)

const mobileRow1Data = testimonials.slice(0, 3)
const mobileRow2Data = testimonials.slice(3, 6)
const mobileRow3Data = testimonials.slice(6, 9)

const leftCol = ref<HTMLElement | null>(null)
const centerCol = ref<HTMLElement | null>(null)
const rightCol = ref<HTMLElement | null>(null)
const mobileRow1 = ref<HTMLElement | null>(null)
const mobileRow2 = ref<HTMLElement | null>(null)
const mobileRow3 = ref<HTMLElement | null>(null)

const tweens = ref<{
  left: gsap.core.Tween | null
  center: gsap.core.Tween | null
  right: gsap.core.Tween | null
  mobile1: gsap.core.Tween | null
  mobile2: gsap.core.Tween | null
  mobile3: gsap.core.Tween | null
}>({
  left: null,
  center: null,
  right: null,
  mobile1: null,
  mobile2: null,
  mobile3: null,
})

const pauseTween = (col: 'left' | 'center' | 'right') => {
  tweens.value[col]?.pause()
}

const resumeTween = (col: 'left' | 'center' | 'right') => {
  tweens.value[col]?.resume()
}

const pauseMobile = (row: number) => {
  const key = `mobile${row}` as 'mobile1' | 'mobile2' | 'mobile3'
  tweens.value[key]?.pause()
}

const resumeMobile = (row: number) => {
  const key = `mobile${row}` as 'mobile1' | 'mobile2' | 'mobile3'
  tweens.value[key]?.resume()
}

onMounted(() => {
  if (leftCol.value) {
    const h = leftCol.value.scrollHeight / 2
    gsap.set(leftCol.value, { y: -h })
    tweens.value.left = gsap.to(leftCol.value, {
      y: 0,
      duration: h / 50,
      ease: 'none',
      repeat: -1,
      modifiers: { y: gsap.utils.unitize((y: string) => parseFloat(y) % h) },
    })
  }

  if (centerCol.value) {
    const h = centerCol.value.scrollHeight / 2
    gsap.set(centerCol.value, { y: 0 })
    tweens.value.center = gsap.to(centerCol.value, {
      y: -h,
      duration: h / 50,
      ease: 'none',
      repeat: -1,
      modifiers: { y: gsap.utils.unitize((y: string) => parseFloat(y) % h) },
    })
  }

  if (rightCol.value) {
    const h = rightCol.value.scrollHeight / 2
    gsap.set(rightCol.value, { y: -h })
    tweens.value.right = gsap.to(rightCol.value, {
      y: 0,
      duration: h / 50,
      ease: 'none',
      repeat: -1,
      modifiers: { y: gsap.utils.unitize((y: string) => parseFloat(y) % h) },
    })
  }

  if (mobileRow1.value) {
    const w = mobileRow1.value.scrollWidth / 2
    gsap.set(mobileRow1.value, { x: -w })
    tweens.value.mobile1 = gsap.to(mobileRow1.value, {
      x: 0,
      duration: w / 40,
      ease: 'none',
      repeat: -1,
      modifiers: { x: gsap.utils.unitize((x: string) => parseFloat(x) % w) },
    })
  }

  if (mobileRow2.value) {
    const w = mobileRow2.value.scrollWidth / 2
    gsap.set(mobileRow2.value, { x: 0 })
    tweens.value.mobile2 = gsap.to(mobileRow2.value, {
      x: -w,
      duration: w / 40,
      ease: 'none',
      repeat: -1,
      modifiers: { x: gsap.utils.unitize((x: string) => parseFloat(x) % w) },
    })
  }

  if (mobileRow3.value) {
    const w = mobileRow3.value.scrollWidth / 2
    gsap.set(mobileRow3.value, { x: -w })
    tweens.value.mobile3 = gsap.to(mobileRow3.value, {
      x: 0,
      duration: w / 40,
      ease: 'none',
      repeat: -1,
      modifiers: { x: gsap.utils.unitize((x: string) => parseFloat(x) % w) },
    })
  }
})
</script>