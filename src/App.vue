<template>
  <Header />
  <main>
    <router-view />
  </main>
  <MultiFooter />
  <Footer />
  <Analytics />
</template>

<script setup lang="ts">
import { Analytics } from '@vercel/analytics/vue'
import Header from './components/Header.vue'
import MultiFooter from './components/MultiFooter.vue'
import Footer from './components/Footer.vue'
</script>