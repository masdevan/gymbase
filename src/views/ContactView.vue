<template>
  <div>
    <section class="relative h-[50vh] min-h-100 flex items-center justify-center overflow-hidden">
      <div class="absolute inset-0 z-0">
        <div class="absolute inset-0 bg-cover bg-center scale-110" style="background-image: url('/hero/image_1.jpg')"></div>
        <div class="absolute inset-0 bg-linear-to-b from-black/80 via-black/60 to-black/90"></div>
      </div>
      <div class="relative z-10 text-center px-4 max-w-4xl mx-auto">
        <h1 class="text-4xl sm:text-5xl md:text-7xl font-extrabold text-white mb-3 sm:mb-4 tracking-tight">Get In <span class="text-[#bbf706]">Touch</span></h1>
        <p class="text-base sm:text-lg md:text-xl text-neutral-300 max-w-2xl mx-auto px-2">Ready to transform your life? Reach out and let's start this journey together.</p>
      </div>
    </section>

    <section class="py-16 sm:py-20 md:py-24 px-4 sm:px-6 md:px-[5%] max-w-7xl mx-auto">
      <div class="flex flex-col lg:flex-row gap-10 md:gap-16">
        <div class="space-y-6 md:space-y-8 w-full lg:w-5/12">
          <div>
            <span class="text-[#bbf706] font-bold uppercase tracking-wider text-xs sm:text-sm">Contact us</span>
            <h2 class="text-2xl sm:text-3xl md:text-4xl font-extrabold text-white mt-2">Let's talk business</h2>
            <div class="w-16 sm:w-20 h-1 bg-[#bbf706] mt-3 sm:mt-4"></div>
          </div>
          <p class="text-neutral-300 text-base sm:text-lg">Have questions about memberships, classes, or just want to know more about our community? We're here to help.</p>
          
          <div class="space-y-5 sm:space-y-6">
            <div class="flex items-start gap-3 sm:gap-4 group">
              <div class="w-10 h-10 sm:w-12 sm:h-12 rounded-lg bg-[#bbf706]/10 flex items-center justify-center group-hover:bg-[#bbf706]/20 transition-colors border border-[#bbf706]/20 shrink-0">
                <MapPinIcon class="w-5 h-5 sm:w-6 sm:h-6 text-[#bbf706]" />
              </div>
              <div>
                <h3 class="text-white font-semibold text-base sm:text-lg">Visit us</h3>
                <p class="text-neutral-400 text-sm sm:text-base">Jl. Raya Boyolali No. 123, Boyolali, Jawa Tengah</p>
              </div>
            </div>
            <div class="flex items-start gap-3 sm:gap-4 group">
              <div class="w-10 h-10 sm:w-12 sm:h-12 rounded-lg bg-[#bbf706]/10 flex items-center justify-center group-hover:bg-[#bbf706]/20 transition-colors border border-[#bbf706]/20 shrink-0">
                <PhoneIcon class="w-5 h-5 sm:w-6 sm:h-6 text-[#bbf706]" />
              </div>
              <div>
                <h3 class="text-white font-semibold text-base sm:text-lg">Call us</h3>
                <p class="text-neutral-400 text-sm sm:text-base">0877-1234-5678</p>
              </div>
            </div>
            <div class="flex items-start gap-3 sm:gap-4 group">
              <div class="w-10 h-10 sm:w-12 sm:h-12 rounded-lg bg-[#bbf706]/10 flex items-center justify-center group-hover:bg-[#bbf706]/20 transition-colors border border-[#bbf706]/20 shrink-0">
                <EnvelopeIcon class="w-5 h-5 sm:w-6 sm:h-6 text-[#bbf706]" />
              </div>
              <div>
                <h3 class="text-white font-semibold text-base sm:text-lg">Email us</h3>
                <p class="text-neutral-400 text-sm sm:text-base">info@gymbase.id</p>
              </div>
            </div>
          </div>
        </div>

        <div class="w-full lg:w-7/12 bg-neutral-900/50 backdrop-blur-sm border border-neutral-800 rounded-2xl p-5 sm:p-6 md:p-8 relative overflow-hidden">
          <div class="absolute top-0 right-0 w-48 h-48 sm:w-64 sm:h-64 bg-[#bbf706]/5 rounded-full blur-3xl z-0"></div>
          <div class="absolute bottom-0 left-0 w-36 h-36 sm:w-48 sm:h-48 bg-[#bbf706]/5 rounded-full blur-3xl z-0"></div>
          
          <div class="relative z-10">
            <h3 class="text-xl sm:text-2xl font-bold text-white mb-1">Send a message</h3>
            <p class="text-neutral-400 text-xs sm:text-sm mb-4 sm:mb-6">Fill out the form and we'll get back to you soon.</p>
            
            <form @submit.prevent="handleSubmit" class="space-y-4 sm:space-y-5">
              <div>
                <label class="block text-neutral-300 text-xs sm:text-sm font-medium mb-1 sm:mb-2">Your name</label>
                <div class="relative">
                  <UserIcon class="absolute left-3 sm:left-4 top-1/2 -translate-y-1/2 w-4 h-4 sm:w-5 sm:h-5 text-neutral-500" />
                  <input type="text" v-model="form.name" required placeholder="John Doe" class="w-full bg-black/50 border border-neutral-700 rounded-lg sm:rounded-xl py-2.5 sm:py-3 pl-9 sm:pl-12 pr-3 sm:pr-4 text-white placeholder:text-neutral-600 text-sm sm:text-base focus:border-[#bbf706] focus:ring-1 focus:ring-[#bbf706] outline-none transition-all">
                </div>
              </div>
              
              <div>
                <label class="block text-neutral-300 text-xs sm:text-sm font-medium mb-1 sm:mb-2">Email address</label>
                <div class="relative">
                  <EnvelopeIcon class="absolute left-3 sm:left-4 top-1/2 -translate-y-1/2 w-4 h-4 sm:w-5 sm:h-5 text-neutral-500" />
                  <input type="email" v-model="form.email" required placeholder="hello@gymbase.id" class="w-full bg-black/50 border border-neutral-700 rounded-lg sm:rounded-xl py-2.5 sm:py-3 pl-9 sm:pl-12 pr-3 sm:pr-4 text-white placeholder:text-neutral-600 text-sm sm:text-base focus:border-[#bbf706] focus:ring-1 focus:ring-[#bbf706] outline-none transition-all">
                </div>
              </div>
              
              <div>
                <label class="block text-neutral-300 text-xs sm:text-sm font-medium mb-1 sm:mb-2">Phone (optional)</label>
                <div class="relative">
                  <PhoneIcon class="absolute left-3 sm:left-4 top-1/2 -translate-y-1/2 w-4 h-4 sm:w-5 sm:h-5 text-neutral-500" />
                  <input type="tel" v-model="form.phone" placeholder="0877-1234-5678" class="w-full bg-black/50 border border-neutral-700 rounded-lg sm:rounded-xl py-2.5 sm:py-3 pl-9 sm:pl-12 pr-3 sm:pr-4 text-white placeholder:text-neutral-600 text-sm sm:text-base focus:border-[#bbf706] focus:ring-1 focus:ring-[#bbf706] outline-none transition-all">
                </div>
              </div>
              
              <div>
                <label class="block text-neutral-300 text-xs sm:text-sm font-medium mb-1 sm:mb-2">Subject</label>
                <div class="relative">
                  <ChatBubbleLeftRightIcon class="absolute left-3 sm:left-4 top-1/2 -translate-y-1/2 w-4 h-4 sm:w-5 sm:h-5 text-neutral-500 pointer-events-none" />
                  <select v-model="form.subject" required class="w-full bg-black/50 border border-neutral-700 rounded-lg sm:rounded-xl py-2.5 sm:py-3 pl-9 sm:pl-12 pr-8 sm:pr-10 text-white placeholder:text-neutral-600 text-sm sm:text-base focus:border-[#bbf706] focus:ring-1 focus:ring-[#bbf706] outline-none appearance-none cursor-pointer">
                    <option value="" disabled selected>Select subject</option>
                    <option value="membership">Membership inquiry</option>
                    <option value="classes">Class information</option>
                    <option value="pt">Personal training</option>
                    <option value="other">Other</option>
                  </select>
                  <ChevronDownIcon class="absolute right-3 sm:right-4 top-1/2 -translate-y-1/2 w-4 h-4 sm:w-5 sm:h-5 text-neutral-500 pointer-events-none" />
                </div>
              </div>
              
              <div>
                <label class="block text-neutral-300 text-xs sm:text-sm font-medium mb-1 sm:mb-2">Message</label>
                <div class="relative">
                  <DocumentTextIcon class="absolute left-3 sm:left-4 top-3 sm:top-4 w-4 h-4 sm:w-5 sm:h-5 text-neutral-500" />
                  <textarea v-model="form.message" rows="4" required placeholder="Tell us how we can help you..." class="w-full bg-black/50 border border-neutral-700 rounded-lg sm:rounded-xl py-2.5 sm:py-3 pl-9 sm:pl-12 pr-3 sm:pr-4 text-white placeholder:text-neutral-600 text-sm sm:text-base focus:border-[#bbf706] focus:ring-1 focus:ring-[#bbf706] outline-none resize-none"></textarea>
                </div>
              </div>
              
              <button type="submit" class="submit-btn w-full bg-[#bbf706] text-black py-2.5 sm:py-3 rounded-lg sm:rounded-xl font-semibold text-sm sm:text-base hover:scale-[1.02] transition-all flex items-center justify-center gap-2 group">
                <span>Send message</span>
                <ArrowRightIcon class="w-4 h-4 group-hover:translate-x-1 transition-transform" />
              </button>
            </form>
          </div>
        </div>
      </div>
    </section>

    <section class="py-8 sm:py-12 px-4 sm:px-6 md:px-[5%] border-t border-neutral-800">
      <div class="max-w-7xl mx-auto">
        <div class="overflow-hidden">
          <iframe 
            src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3957.567891234567!2d110.621!3d-7.533!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x2e7a1f6b7c8d9e0f%3A0x123456789abcdef!2sBoyolali%2C%20Jawa%20Tengah!5e0!3m2!1sid!2sid!4v1234567890123!5m2!1sid!2sid" 
            width="100%" 
            height="300" 
            style="border:0; filter: brightness(0.7) contrast(1.2) saturate(0.8);" 
            loading="lazy"
            referrerpolicy="no-referrer-when-downgrade">
          </iframe>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { gsap } from 'gsap'
import { MapPinIcon, PhoneIcon, EnvelopeIcon, ArrowRightIcon, ChevronDownIcon, UserIcon, ChatBubbleLeftRightIcon, DocumentTextIcon } from '@heroicons/vue/24/outline'

const form = ref({
  name: '',
  email: '',
  phone: '',
  subject: '',
  message: ''
})

const handleSubmit = () => {
  alert('Thank you for reaching out! We will get back to you within 24 hours.')
  form.value = { name: '', email: '', phone: '', subject: '', message: '' }
}

onMounted(() => {
  gsap.from('.text-5xl', { opacity: 0, y: 60, duration: 0.8, ease: 'power3.out' })
  gsap.from('.text-xl', { opacity: 0, y: 30, duration: 0.6, delay: 0.3 })
  gsap.from('.space-y-8', { opacity: 0, x: -50, duration: 0.7 })
  gsap.from('.bg-neutral-900\\/50', { opacity: 0, x: 50, duration: 0.7 })
  gsap.from('.submit-btn', { opacity: 0, scale: 0.9, duration: 0.5 })
})
</script>