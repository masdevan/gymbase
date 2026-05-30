<template>
  <Header />
  <main>
    <router-view />
  </main>
  <MultiFooter />
  <Footer />
</template>

<script setup lang="ts">
import Header from './components/Header.vue'
import MultiFooter from './components/MultiFooter.vue'
import Footer from './components/Footer.vue'
</script>