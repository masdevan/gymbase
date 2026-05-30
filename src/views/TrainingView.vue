<template>
  <div>
    <section class="relative h-[60vh] min-h-125 flex items-center justify-center overflow-hidden">
      <div class="absolute inset-0 z-0">
        <div class="absolute inset-0 bg-cover bg-center scale-110" style="background-image: url('/hero/image_1.jpg')"></div>
        <div class="absolute inset-0 bg-linear-to-b from-black/80 via-black/60 to-black/90"></div>
      </div>
      <div class="relative z-10 text-center px-4 max-w-4xl mx-auto">
        <h1 class="text-5xl md:text-7xl font-extrabold text-white mb-4 tracking-tight">Elite <span class="text-[#bbf706]">Coaching</span></h1>
        <p class="text-lg md:text-xl text-neutral-300 max-w-2xl mx-auto">World-class trainers who will push you beyond your limits.</p>
      </div>
    </section>

    <section class="py-24 px-4 sm:px-6 md:px-[5%] max-w-7xl mx-auto">
      <div class="text-center mb-16">
        <span class="text-[#bbf706] font-bold uppercase tracking-wider text-sm">One on One</span>
        <h2 class="text-4xl md:text-6xl font-extrabold text-white mt-2">Personal Trainers</h2>
        <p class="text-neutral-400 max-w-2xl mx-auto mt-4">Tailored programs, accountability, and the motivation you need to crush your goals.</p>
      </div>

      <div class="flex flex-col gap-20">
        <div v-for="(trainer, index) in personalTrainers" :key="trainer.name" 
             class="group flex flex-col md:flex-row gap-8 items-center" :class="index % 2 === 1 ? 'md:flex-row-reverse' : ''">
          <div class="w-full md:w-1/2 relative overflow-hidden rounded-2xl">
            <div class="aspect-3/4 overflow-hidden rounded-2xl">
              <img :src="trainer.image" :alt="trainer.name" class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-105">
            </div>
            <div class="absolute inset-0 bg-linear-to-r from-black/50 to-transparent rounded-2xl"></div>
          </div>
          <div class="w-full md:w-1/2 space-y-4">
            <div class="flex items-center gap-3">
              <span class="text-[#bbf706] font-bold tracking-wide">{{ trainer.specialty }}</span>
            </div>
            <h3 class="text-4xl md:text-5xl font-black text-white tracking-tight">{{ trainer.name }}</h3>
            <p class="text-neutral-300 text-lg leading-relaxed">{{ trainer.bio }}</p>
            <div class="flex items-center gap-4 pt-2">
              <div class="flex items-center gap-2">
                <StarIcon class="w-5 h-5 text-[#bbf706]" />
                <span class="text-neutral-400">{{ trainer.experience }} years experience</span>
              </div>
            </div>
            <a :href="`https://wa.me/6287712345678?text=${encodeURIComponent(`Hi, I'm interested in training with ${trainer.name.split(' ')[0]} at Gymbase. Can I get more information?`)}`" 
               target="_blank"
               rel="noopener noreferrer"
               class="mt-4 inline-flex items-center gap-2 text-[#bbf706] border border-[#bbf706] px-4 py-2 rounded-full hover:gap-3 transition-all">
              Train with {{ trainer.name.split(' ')[0] }} 
              <ArrowRightIcon class="w-4 h-4" />
            </a>
          </div>
        </div>
      </div>
    </section>

    <section class="py-24 px-4 sm:px-6 md:px-[5%] bg-neutral-900/30 relative overflow-hidden">
      <div class="absolute inset-0 opacity-5 bg-[url('/hero/image_3.jpg')] bg-cover bg-fixed"></div>
      <div class="max-w-7xl mx-auto relative z-10">
        <div class="text-center mb-16">
          <span class="text-[#bbf706] font-bold uppercase tracking-wider text-sm">Iron sharpens iron</span>
          <h2 class="text-4xl md:text-6xl font-extrabold text-white mt-2">Strength Coaches</h2>
          <p class="text-neutral-400 max-w-2xl mx-auto mt-4">Powerlifting, olympic lifting, strongman – get brutally strong under expert guidance.</p>
        </div>

        <div class="flex flex-col gap-20">
          <div v-for="(trainer, index) in strengthTrainers" :key="trainer.name" 
               class="group flex flex-col md:flex-row gap-8 items-center" :class="index % 2 === 1 ? 'md:flex-row-reverse' : ''">
            <div class="w-full md:w-1/2 relative overflow-hidden rounded-2xl">
              <div class="aspect-3/4 overflow-hidden rounded-2xl">
                <img :src="trainer.image" :alt="trainer.name" class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-105">
              </div>
              <div class="absolute inset-0 bg-linear-to-r from-black/50 to-transparent rounded-2xl"></div>
            </div>
            <div class="w-full md:w-1/2 space-y-4">
              <div class="flex items-center gap-3">
                <span class="text-[#bbf706] font-bold tracking-wide">{{ trainer.specialty }}</span>
              </div>
              <h3 class="text-4xl md:text-5xl font-black text-white tracking-tight">{{ trainer.name }}</h3>
              <p class="text-neutral-300 text-lg leading-relaxed">{{ trainer.bio }}</p>
              <div class="flex items-center gap-4 pt-2">
                <div class="flex items-center gap-2">
                  <TrophyIcon class="w-5 h-5 text-[#bbf706]" />
                  <span class="text-neutral-400">{{ trainer.certification }}</span>
                </div>
                <div class="flex items-center gap-2">
                  <ChartBarIcon class="w-5 h-5 text-[#bbf706]" />
                  <span class="text-neutral-400">{{ trainer.maxLift }}</span>
                </div>
              </div>
              <a :href="`https://wa.me/6287712345678?text=${encodeURIComponent(`Hi, I'm interested in training with ${trainer.name.split(' ')[0]} at Gymbase. Can I get more information?`)}`" 
                 target="_blank"
                 rel="noopener noreferrer"
                 class="mt-4 inline-flex items-center gap-2 text-[#bbf706] hover:gap-3 border border-[#bbf706] px-4 py-2 rounded-full transition-all">
                Train with {{ trainer.name.split(' ')[0] }} 
                <ArrowRightIcon class="w-4 h-4" />
              </a>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="py-24 px-4 text-center relative overflow-hidden">
      <div class="absolute inset-0 bg-[url('/hero/image_2.jpg')] bg-cover bg-center opacity-10"></div>
      <div class="relative z-10 max-w-3xl mx-auto">
        <h2 class="text-4xl md:text-6xl font-extrabold text-white mb-4">Ready to level up?</h2>
        <p class="text-neutral-300 text-lg mb-8">Get matched with the perfect coach for your goals.</p>
        <router-link to="/contact" class="inline-flex items-center gap-2 bg-[#bbf706] text-black px-8 py-4 rounded-full font-bold text-lg hover:scale-105 transition-transform">
          Start your journey
          <ArrowRightIcon class="w-5 h-5" />
        </router-link>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
import { StarIcon, TrophyIcon, ChartBarIcon, ArrowRightIcon } from '@heroicons/vue/24/outline'

const personalTrainers = [
  {
    name: 'Mega Fitriani',
    specialty: 'Weight Loss & Lifestyle',
    bio: 'Mega combines nutrition science with functional training to help you shed fat and keep it off. She’s transformed over 200 clients.',
    experience: 8,
    image: '/trainer/woman_1.jpg'
  },
  {
    name: 'Michael Santoso',
    specialty: 'CrossFit & Endurance',
    bio: 'Level 2 CrossFit coach with a passion for conditioning. He’ll build your engine and mental toughness.',
    experience: 6,
    image: '/trainer/men_1.jpg'
  },
  {
    name: 'Fitri Kurniawan',
    specialty: 'Rehab & Mobility',
    bio: 'Post-injury and chronic pain specialist. Nina uses corrective exercises to get you moving freely again.',
    experience: 5,
    image: '/trainer/woman_2.jpg'
  },
  {
    name: 'Kondi Bagas',
    specialty: 'Functional Fitness',
    bio: 'Certified functional trainer. Helps clients build real-world strength and endurance for daily life.',
    experience: 7,
    image: '/trainer/men_2.jpg'
  },
  {
    name: 'Surat Sutrisno',
    specialty: 'Pre & Post Natal',
    bio: 'Specialist in pre and post natal fitness. Safe, effective workouts for every trimester.',
    experience: 9,
    image: '/trainer/men_3.jpg'
  },
  {
    name: 'April Dewi',
    specialty: 'Senior Fitness',
    bio: 'Focus on mobility, balance, and strength for active aging. Keeps you moving pain-free.',
    experience: 10,
    image: '/trainer/woman_3.jpg'
  }
]

const strengthTrainers = [
  {
    name: 'Alex Nurdiansyah',
    specialty: 'Powerlifting & Strongman',
    bio: 'IPF national medalist with a 650lb deadlift. Alex programs raw strength and mental grit.',
    certification: 'IPF Elite Coach',
    maxLift: '650lbs deadlift',
    image: '/trainer/men_4.jpg'
  },
  {
    name: 'Sohibul Hadi',
    specialty: 'Olympic Weightlifting',
    bio: 'Former national champion in 81kg class. Rizky’s technique is unmatched – pure poetry.',
    certification: 'USAW Level 2',
    maxLift: '120kg snatch',
    image: '/trainer/men_5.jpg'
  },
  {
    name: 'Cece Setiawati',
    specialty: 'Speed & Agility',
    bio: 'NSCA certified S&C coach. Build explosive power, faster sprint times, and resilience.',
    certification: 'NSCA CSCS',
    maxLift: '40 inch vertical',
    image: '/trainer/woman_4.jpg'
  },
  {
    name: 'Rere Belinda',
    specialty: 'Bodybuilding',
    bio: 'IFBB pro physique competitor. Sculpting aesthetics with science-based hypertrophy methods.',
    certification: 'NASM CPT',
    maxLift: '315lbs squat',
    image: '/trainer/woman_5.jpg'
  },
  {
    name: 'Farah Valentina',
    specialty: 'Strongman',
    bio: 'National strongman competitor. Yoke walks, atlas stones, and log press specialist.',
    certification: 'Strongman Corp',
    maxLift: '350lbs log press',
    image: '/trainer/woman_6.jpg'
  },
  {
    name: 'Sigit Prasetyo',
    specialty: 'Kettlebell & Girevoy',
    bio: 'Certified kettlebell instructor. Builds explosive hip power and bulletproof shoulders.',
    certification: 'RKC Level 2',
    maxLift: '48kg clean & jerk',
    image: '/trainer/men_6.jpg'
  }
]
</script>