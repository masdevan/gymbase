<template>
  <div class="flex justify-between items-center px-[5%] py-3 bg-black text-neutral-400 text-xs border-b border-neutral-800">
    <span>Gymbase in Boyolali, Indonesia</span>
    <span>Jon: 0877-1234-5678</span>
  </div>
  <header
    ref="headerRef"
    class="sticky top-0 z-50 flex justify-between items-center px-[5%] py-5 bg-neutral-950 border-b border-transparent transition-colors duration-300"
    :class="{ 'border-neutral-800 bg-neutral-950/95 backdrop-blur-md': scrolled }"
  >
    <router-link to="/" class="flex items-center gap-3 text-2xl font-extrabold leading-tight tracking-tight">
      <img src="/core/logo.png" alt="Gymbase" class="w-8 h-8" />
      <span>Gymbase</span>
    </router-link>
    <button class="text-3xl lg:hidden relative w-8 h-8 flex items-center justify-center" @click="toggleMenu">
      <span class="absolute transition-transform duration-300" :class="{ 'rotate-90 opacity-0': isOpen, 'rotate-0 opacity-100': !isOpen }">☰</span>
      <span class="absolute transition-transform duration-300" :class="{ 'rotate-0 opacity-100': isOpen, 'rotate-90 opacity-0': !isOpen }">✕</span>
    </button>
    <nav class="hidden lg:flex items-center gap-8">
      <router-link to="/membership" class="text-sm font-medium hover:text-[#bbf706] transition-colors">Membership</router-link>
      <router-link to="/services" class="text-sm font-medium hover:text-[#bbf706] transition-colors">Services</router-link>
      <router-link to="/about" class="text-sm font-medium hover:text-[#bbf706] transition-colors">About</router-link>
      <router-link to="/contact" class="text-sm font-medium hover:text-[#bbf706] transition-colors">Contact</router-link>
    </nav>
    <router-link to="/contact" class="hidden lg:inline-block bg-[#bbf706] text-black px-6 py-3 rounded-full text-sm font-semibold hover:scale-105 transition-transform">Ready To Fight</router-link>
    <transition name="menu-slide">
      <div v-if="isOpen" class="absolute top-full left-0 w-full lg:hidden bg-neutral-950/95 backdrop-blur-md border-b border-neutral-800">
        <div class="flex flex-col gap-6 p-8">
          <a href="/membership" @click="closeMenu" class="text-base font-medium">Membership</a>
          <router-link to="/services" @click="closeMenu" class="text-base font-medium">Services</router-link>
          <router-link to="/about" @click="closeMenu" class="text-base font-medium">About</router-link>
          <router-link to="/contact" @click="closeMenu" class="text-base font-medium">Contact</router-link>
          <a href="/contact" @click="closeMenu" class="bg-[#bbf706] text-black px-6 py-3 rounded-full text-sm font-semibold text-center mt-4">Ready To Fight</a>
        </div>
      </div>
    </transition>
  </header>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted, nextTick } from 'vue'

const isOpen = ref(false)
const scrolled = ref(false)
const headerRef = ref<HTMLElement | null>(null)

const updateHeaderHeight = () => {
  const topBar = headerRef.value?.previousElementSibling as HTMLElement | null
  const topHeight = topBar?.offsetHeight ?? 0
  const headerHeight = headerRef.value?.offsetHeight ?? 0
  document.documentElement.style.setProperty('--header-height', `${topHeight + headerHeight}px`)
}

const onScroll = () => {
  scrolled.value = window.scrollY > 50
}

const toggleMenu = () => {
  isOpen.value = !isOpen.value
  nextTick(() => updateHeaderHeight()) 
}

const closeMenu = () => {
  isOpen.value = false
}

onMounted(() => {
  updateHeaderHeight()
  window.addEventListener('resize', updateHeaderHeight)
  window.addEventListener('scroll', onScroll)
})

onUnmounted(() => {
  window.removeEventListener('resize', updateHeaderHeight)
  window.removeEventListener('scroll', onScroll)
})
</script>

<style scoped>
.menu-slide-enter-active {
  animation: slideDown 0.3s ease-out;
}
.menu-slide-leave-active {
  animation: slideUp 0.2s ease-in;
}
@keyframes slideDown {
  from { opacity: 0; transform: translateY(-10px); }
  to { opacity: 1; transform: translateY(0); }
}
@keyframes slideUp {
  from { opacity: 1; transform: translateY(0); }
  to { opacity: 0; transform: translateY(-10px); }
}
</style>