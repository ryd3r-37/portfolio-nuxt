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
    
<aside class="sticky top-0 h-auto md:h-screen w-full md:w-[240px] bg-[#141416] border-b md:border-b-0 md:border-r border-[#2a2a2a] p-5 flex flex-row md:flex-col justify-between items-center z-50">
  
  <div class="w-full flex md:flex-col items-center justify-between md:justify-start gap-4">
    <div class="w-full flex items-center justify-between">
      <NuxtLink to="/" class="block transition hover:scale-105 active:scale-95 shrink-0">
        <div class="w-16 h-16 bg-[#2a2a2a] rounded-[14px] flex items-center justify-center border border-[#333] overflow-hidden">
          <img src="/images/background/logo.png" alt="Logo" class="w-full h-full object-cover" />
        </div>
      </NuxtLink>

      <div class="hidden md:block">
        <label for="theme-toggle" class="switch cursor-pointer inline-block relative w-[3.2em] h-[1.8em]">
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
    </div>

    <div class="flex items-center gap-3 md:hidden">
      <label for="theme-toggle-mobile" class="switch cursor-pointer inline-block relative w-[3em] h-[1.7em]">
        <span class="sr-only">Toggle dark/light theme</span>
        <input 
          id="theme-toggle-mobile" 
          type="checkbox" 
          :checked="isLightMode" 
          @change="toggleTheme" 
          class="opacity-0 w-0 h-0" 
        />
        <span class="slider absolute cursor-pointer inset-0 bg-[#20262c] transition-all duration-500 rounded-[30px]"></span>
      </label>
      <button @click="navOpen = !navOpen" class="cursor-pointer flex flex-col gap-1.5 p-2 bg-transparent border-none" aria-label="Toggle Navigation Menu">
        <span class="block w-6 h-0.5 bg-[#bbb] transition-all duration-300" :class="{ 'rotate-45 translate-y-2 bg-[#ff3b3b]': navOpen }"></span>
        <span class="block w-6 h-0.5 bg-[#bbb] transition-all duration-300" :class="{ 'opacity-0': navOpen }"></span>
        <span class="block w-6 h-0.5 bg-[#bbb] transition-all duration-300" :class="{ '-rotate-45 -translate-y-2 bg-[#ff3b3b]': navOpen }"></span>
      </button>
    </div>
  </div>

  <div :class="navOpen ? 'flex' : 'hidden'" class="md:flex flex-col items-center gap-4 w-full my-auto py-6 absolute md:static top-full left-0 bg-[#141416] md:bg-transparent p-5 md:p-0 border-b border-[#2a2a2a] md:border-none z-40">
    <div class="text-xs font-mono uppercase tracking-widest text-[#ff3b3b] font-bold mb-1">Navigation</div>
    <nav class="flex flex-col items-center gap-3 w-full">
      <NuxtLink to="/" class="text-sm font-medium text-[#bbb] hover:text-[#ff3b3b] transition hover:scale-105" active-class="!text-[#ff3b3b] font-semibold">Home</NuxtLink>
      <NuxtLink to="/about" class="text-sm font-medium text-[#bbb] hover:text-[#ff3b3b] transition hover:scale-105" active-class="!text-[#ff3b3b] font-semibold">About</NuxtLink>
      <NuxtLink to="/techstack" class="text-sm font-medium text-[#bbb] hover:text-[#ff3b3b] transition hover:scale-105" active-class="!text-[#ff3b3b] font-semibold">Tech Stack</NuxtLink>
      <NuxtLink to="/certification" class="text-sm font-medium text-[#bbb] hover:text-[#ff3b3b] transition hover:scale-105" active-class="!text-[#ff3b3b] font-semibold">Certifications</NuxtLink>
    </nav>
  </div>

  <div class="hidden md:flex flex-col items-center gap-3 w-full pt-4 border-t border-[#2a2a2a]">
    <div class="text-[10px] font-mono text-[#888] uppercase tracking-wider">Connect</div>
    <div class="flex items-center justify-center gap-3">
      <a 
        href="https://github.com/ryd3r-37" 
        target="_blank" 
        rel="noopener noreferrer"
        class="w-9 h-9 rounded-lg bg-[#1a1a1c] border border-[#2a2a2a] flex items-center justify-center text-[#bbb] hover:text-white hover:border-[#ff3b3b]/50 hover:bg-[#ff3b3b]/10 transition"
        title="GitHub Profile"
      >
        <svg class="w-4 h-4 fill-current" viewBox="0 0 24 24">
          <path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0024 12c0-6.63-5.37-12-12-12z"/>
        </svg>
      </a>

      <a 
        href="https://linkedin.com" 
        target="_blank" 
        rel="noopener noreferrer"
        class="w-9 h-9 rounded-lg bg-[#1a1a1c] border border-[#2a2a2a] flex items-center justify-center text-[#bbb] hover:text-white hover:border-[#ff3b3b]/50 hover:bg-[#ff3b3b]/10 transition"
        title="LinkedIn Profile"
      >
        <svg class="w-4 h-4 fill-current" viewBox="0 0 24 24">
          <path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/>
        </svg>
      </a>
    </div>
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