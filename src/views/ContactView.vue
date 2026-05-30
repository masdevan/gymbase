<template>
  <section class="py-24 px-[5%] max-w-7xl mx-auto">
    <div class="grid lg:grid-cols-2 gap-12 bg-neutral-900 p-8 lg:p-16 rounded-3xl border border-neutral-800 contact-wrapper">
      <div ref="contactInfo">
        <p class="text-[#bbf706] font-semibold uppercase tracking-wider text-sm mb-4">About Gymbase</p>
        <h2 class="text-5xl font-extrabold leading-tight mb-6 text-white">Hi! We're a local CrossFit gym in Boyolali, Indonesia.</h2>
        <p class="text-neutral-400 text-lg">Gymbase was started by Alex and Sparky in 2012. It's our mission to help people in Boyolali get fit, stay healthy, and live life on their terms without fitness being an obstacle.</p>
      </div>
      <div ref="contactForm">
        <h3 class="text-2xl font-bold mb-8 text-white">Claim your 7 day free trial</h3>
        <form @submit.prevent class="space-y-5">
          <div>
            <label class="block text-sm text-neutral-400 mb-2">Name*</label>
            <input type="text" required class="w-full bg-black border border-neutral-700 rounded-lg p-4 text-white focus:border-[#bbf706] outline-none transition-colors">
          </div>
          <div>
            <label class="block text-sm text-neutral-400 mb-2">Email*</label>
            <input type="email" required class="w-full bg-black border border-neutral-700 rounded-lg p-4 text-white focus:border-[#bbf706] outline-none transition-colors">
          </div>
          <div>
            <label class="block text-sm text-neutral-400 mb-2">Phone number*</label>
            <input type="tel" required class="w-full bg-black border border-neutral-700 rounded-lg p-4 text-white focus:border-[#bbf706] outline-none transition-colors">
          </div>
          <div>
            <label class="block text-sm text-neutral-400 mb-2">Membership interest...*</label>
            <select required class="w-full bg-black border border-neutral-700 rounded-lg p-4 text-white focus:border-[#bbf706] outline-none transition-colors appearance-none bg-[url('data:image/svg+xml;charset=US-ASCII,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%22292.4%22%20height%3D%22292.4%22%3E%3Cpath%20fill%3D%22%23FFFFFF%22%20d%3D%22M287%2069.4a17.6%2017.6%200%200%200-13-5.4H18.4c-5%200-9.3%201.8-12.9%205.4A17.6%2017.6%200%200%200%200%2082.2c0%205%201.8%209.3%205.4%2012.9l128%20127.9c3.6%203.6%207.8%205.4%2012.8%205.4s9.2-1.8%2012.8-5.4L287%2095c3.5-3.5%205.4-7.8%205.4-12.8%200-5-1.9-9.2-5.5-12.8z%22%2F%3E%3C%2Fsvg%3E')] bg-no-repeat bg-[right_16px_top_50%] bg-[length:12px_auto]">
              <option value="" disabled selected>Select an option</option>
              <option value="month">Month to Month</option>
              <option value="six">6 Month</option>
              <option value="year">1 Year</option>
              <option value="else">Else</option>
            </select>
          </div>
          <button type="submit" class="w-full bg-[#bbf706] text-black py-4 rounded-full font-semibold hover:scale-105 transition-transform">Submit</button>
        </form>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { gsap } from 'gsap'

const contactInfo = ref(null)
const contactForm = ref(null)

onMounted(() => {
  gsap.from(contactInfo.value, {
    opacity: 0,
    x: -40,
    duration: 0.8,
    ease: 'power2.out'
  })
  gsap.from(contactForm.value, {
    opacity: 0,
    x: 40,
    duration: 0.8,
    ease: 'power2.out',
    delay: 0.2
  })
})
</script>