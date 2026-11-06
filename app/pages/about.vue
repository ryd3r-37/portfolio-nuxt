<script setup>
import { ref, onMounted } from 'vue'

const isLightMode = ref(false)
const navOpen = ref(false)

onMounted(() => {
  if (import.meta.client && localStorage.getItem('theme') === 'light') {
    isLightMode.value = true
    document.documentElement.classList.add('light-mode')
  }
})

const toggleTheme = () => {
  isLightMode.value = !isLightMode.value
  if (import.meta.client) {
    if (isLightMode.value) {
      localStorage.setItem('theme', 'light')
      document.documentElement.classList.add('light-mode')
    } else {
      localStorage.setItem('theme', 'dark')
      document.documentElement.classList.remove('light-mode')
    }
  }
}

const techPillars = ref([
  { title: 'Database Optimization', desc: 'Relational schema design, SQL query tuning, and entity relationship modeling.' },
  { title: 'Full-Stack Development', desc: 'Building responsive web interfaces backed by structured database services.' },
  { title: 'Mobile Solutions', desc: 'Developing practical mobile features and local database synchronization.' }
])

const coreSkills = ref([
  'PostgreSQL', 'MS SQL Server', 'Java Swing', 'Android Studio', 'Nuxt 3', 'Tailwind CSS', 'Git'
])

const roadmap = ref([
  { step: '01', goal: 'Schema Optimization' },
  { step: '02', goal: 'Full-Stack Application Delivery' },
  { step: '03', goal: 'Mobile Solutions' }
])
</script>

<template>
  <div :class="{ 'light-mode': isLightMode }" class="bg-[#0f0f10] text-[#ddd] flex min-h-screen flex-col md:flex-row font-inter transition-colors duration-300">
    
    <aside class="sticky top-0 h-auto md:h-screen w-full md:w-[230px] bg-[#141416] border-b md:border-b-0 md:border-r border-[#2a2a2a] p-4 md:p-5 flex flex-row md:flex-col items-center justify-between md:justify-center gap-4 z-50">
      <NuxtLink to="/" class="block transition hover:scale-105 active:scale-95 shrink-0">
        <div class="w-20 h-20 bg-[#2a2a2a] rounded-[14px] flex items-center justify-center border border-[#333] overflow-hidden">
          <img src="/images/background/logo.png" alt="Logo" class="w-full h-full object-cover" />
        </div>
      </NuxtLink>

      <div class="md:absolute md:top-4 md:right-4 z-10 ml-auto mr-4 md:mr-0 md:ml-0">
        <label for="theme-toggle" class="switch cursor-pointer inline-block relative w-[3.5em] h-[2em]">
          <span class="sr-only">Toggle dark/light theme</span>
          <input 
            id="theme-toggle" 
            type="checkbox" 
            :checked="isLightMode" 
            @change="toggleTheme" 
            class="opacity-0 w-0 h-0" 
          />
          <span class="slider absolute cursor-pointer inset-0 bg-[#20262c] transition-all duration-500 rounded-[30px]"></span>
        </label>
      </div>
      
      <button @click="navOpen = !navOpen" class="md:hidden cursor-pointer flex flex-col gap-1.5 p-2 z-50 bg-transparent border-none" aria-label="Toggle Navigation Menu">
        <span class="block w-6 h-0.5 bg-[#bbb] transition-all duration-300" :class="{ 'rotate-45 translate-y-2 bg-[#ff3b3b]': navOpen }"></span>
        <span class="block w-6 h-0.5 bg-[#bbb] transition-all duration-300" :class="{ 'opacity-0': navOpen }"></span>
        <span class="block w-6 h-0.5 bg-[#bbb] transition-all duration-300" :class="{ '-rotate-45 -translate-y-2 bg-[#ff3b3b]': navOpen }"></span>
      </button>
      
      <div :class="navOpen ? 'flex' : 'hidden'" class="md:flex flex-col items-center gap-4 absolute md:static top-full left-0 w-full bg-[#141416] md:bg-transparent p-5 md:p-0 border-b border-[#2a2a2a] md:border-none z-40">
        <div class="text-base font-bold text-[#ff3b3b] hidden md:block">Menu</div>
        <nav class="flex flex-col items-center gap-3 md:gap-2">
          <NuxtLink to="/" class="text-sm text-[#bbb] hover:text-[#ff3b3b] transition hover:translate-x-1">Home</NuxtLink>
          <NuxtLink to="/about" class="text-sm text-[#ff3b3b] font-semibold transition hover:translate-x-1">About</NuxtLink>
          <NuxtLink to="/techstack" class="text-sm text-[#bbb] hover:text-[#ff3b3b] transition hover:translate-x-1">Tech Stack</NuxtLink>
          <NuxtLink to="/certification" class="text-sm text-[#bbb] hover:text-[#ff3b3b] transition hover:translate-x-1">Certifications</NuxtLink>
        </nav>
      </div>
    </aside>

    <main class="flex-1 p-5 md:p-10 flex justify-center items-center">
      <div class="w-full max-w-[950px] space-y-6">
        
        <div class="flex items-center justify-between border-b border-[#2a2a2a] pb-4">
          <div>
            <span class="text-xs font-mono text-[#ff3b3b] tracking-wider uppercase">Portfolio // Developer Profile</span>
            <h1 class="text-3xl md:text-4xl font-extrabold text-white mt-1">About Me</h1>
          </div>
          <div class="hidden sm:block text-right">
            <span class="inline-block w-2.5 h-2.5 bg-[#ff3b3b] rounded-full animate-pulse mr-2"></span>
            <span class="text-xs text-[#888] font-mono">BSIT / SDCA</span>
          </div>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">

          <section class="lg:col-span-2 rounded-2xl border border-[#2a2a2a] p-6 md:p-8 bg-[#141416] shadow-xl flex flex-col justify-between">
            <div>
              <div class="flex items-center gap-2 mb-4">
                <span class="px-2.5 py-0.5 rounded bg-[#ff3b3b]/10 text-[#ff3b3b] text-xs font-mono border border-[#ff3b3b]/30">Overview</span>
              </div>
              <h2 class="text-xl md:text-2xl font-bold text-white mb-4">Building backend precision with modern user interfaces.</h2>
              <p class="text-sm text-[#bbb] leading-relaxed mb-4">
                As a 3rd-year Information Technology student, I focus heavily on relational database architecture, SQL optimization, and end-to-end software development.
              </p>
              <p class="text-sm text-[#bbb] leading-relaxed">
                I enjoy tackling complex schema designs and engineering responsive applications ensuring backend data is structured cleanly while frontend experiences remain fast and fluid.
              </p>
            </div>

            <div class="grid grid-cols-1 sm:grid-cols-3 gap-3 mt-8 pt-6 border-t border-[#2a2a2a]">
              <div v-for="pillar in techPillars" :key="pillar.title" class="space-y-1">
                <h3 class="text-xs font-bold text-white uppercase tracking-wider">{{ pillar.title }}</h3>
                <p class="text-[11px] text-[#888] leading-normal">{{ pillar.desc }}</p>
              </div>
            </div>
          </section>

          <section class="rounded-2xl border border-[#2a2a2a] p-6 bg-[#141416] shadow-xl flex flex-col justify-between">
            <div>
              <div class="flex items-center gap-2 mb-4">
                <span class="px-2.5 py-0.5 rounded bg-[#ff3b3b]/10 text-[#ff3b3b] text-xs font-mono border border-[#ff3b3b]/30">Stack</span>
              </div>
              <h2 class="text-lg font-bold text-white mb-3">Tools</h2>
              <p class="text-xs text-[#888] leading-relaxed mb-6">
                Key technologies I work with across database management, desktop, web, and mobile development.
              </p>
              
              <div class="flex flex-wrap gap-2">
                <span 
                  v-for="skill in coreSkills" 
                  :key="skill"
                  class="px-3 py-1 rounded-md bg-[#1a1a1c] border border-[#2a2a2a] text-[#ddd] text-xs font-mono hover:border-[#ff3b3b]/50 transition cursor-default"
                >
                  {{ skill }}
                </span>
              </div>
            </div>

            <div class="mt-6 pt-4 border-t border-[#2a2a2a] text-right">
              <NuxtLink to="/techstack" class="text-xs font-semibold text-[#ff3b3b] hover:underline inline-flex items-center gap-1">
                View Full Tech Stack &rarr;
              </NuxtLink>
            </div>
          </section>

        </div>

        <section class="rounded-2xl border border-[#2a2a2a] p-6 bg-[#141416] shadow-xl">
          <div class="flex flex-col sm:flex-row sm:items-center justify-between mb-6 gap-2">
            <div>
              <span class="text-xs font-mono text-[#ff3b3b] uppercase">Goals</span>
              <h2 class="text-xl font-bold text-white">Current Technical Objectives</h2>
            </div>
            <span class="text-xs text-[#888] font-mono">Continuous Growth</span>
          </div>

          <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
            <div 
              v-for="item in roadmap" 
              :key="item.step"
              class="p-4 rounded-xl bg-[#1a1a1c] border border-[#2a2a2a] flex items-center gap-4 hover:border-[#ff3b3b]/40 transition"
            >
              <span class="text-lg font-bold text-[#ff3b3b] font-mono shrink-0">{{ item.step }}</span>
              <p class="text-xs font-semibold text-[#ddd] leading-snug">{{ item.goal }}</p>
            </div>
          </div>
        </section>

      </div>
    </main>

  </div>
</template>