<template>
  <div class="group bg-neutral-900 border border-neutral-800 hover:border-[#bbf706] rounded-2xl p-6 flex flex-col transition-all duration-300 hover:-translate-y-1">
    <div class="flex items-center gap-4 mb-5">
      <div class="relative">
        <img :src="item.image" :alt="item.name" class="w-14 h-14 rounded-full object-cover" />
        <div class="absolute -bottom-1 -right-1 w-5 h-5 bg-green-500 rounded-full border-2 border-neutral-900" title="Verified Member"></div>
      </div>
      <div>
        <p class="text-white font-semibold text-lg">{{ item.name }}</p>
        <p class="text-neutral-500 text-sm">{{ item.location }} · {{ item.duration }}</p>
      </div>
    </div>
    <p class="text-neutral-300 italic text-base leading-relaxed">"{{ item.quote }}"</p>
  </div>
</template>

<script setup lang="ts">
interface Testimonial {
  image: string
  name: string
  location: string
  duration: string
  quote: string
}
defineProps<{ item: Testimonial }>()
</script>