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

const certifications = ref([
  {
    title: 'Microsoft Word Associate',
    issuer: 'Certiport',
    date: 'May 2026',
    code: 'CERT-WORD-2026',
    desc: 'Demonstrates certified proficiency in document design, structural formatting, and executive output standards.',
    badge: '/images/personal/CertDatabase_page-0001.jpg'
  },
  {
    title: 'Specialist in Java',
    issuer: 'Certiport',
    date: 'May 2026',
    code: 'CERT-JAVA-2026',
    desc: 'Demonstrates foundational competence in Java programming logic, object-oriented principles, and application structure.',
    badge: '/images/personal/CertJava_page-0001.jpg'
  },
  {
    title: 'IT Specialist - Databases',
    issuer: 'Certiport | Pearson VUE',
    date: 'June 2026',
    code: 'CERT-DATABASE-2026',
    desc: 'Validates core database management skills, relational schema concepts, SQL query execution, and data integrity principles.',
    badge: '/images/personal/CertDatabase_page-0001.jpg'
  }
])
</script>

<template>
  <div :class="{ 'light-mode': isLightMode }" class="bg-[#0f0f10] text-[#ddd] flex min-h-screen flex-col md:flex-row font-inter transition-colors duration-300 relative overflow-hidden">
    
    <div class="absolute -top-32 -right-32 w-96 h-96 bg-[#ff3b3b]/10 rounded-full blur-3xl pointer-events-none"></div>
    <div class="absolute -bottom-32 -left-32 w-96 h-96 bg-[#ff3b3b]/5 rounded-full blur-3xl pointer-events-none"></div>

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
          <NuxtLink to="/about" class="text-sm text-[#bbb] hover:text-[#ff3b3b] transition hover:translate-x-1">About</NuxtLink>
          <NuxtLink to="/techstack" class="text-sm text-[#bbb] hover:text-[#ff3b3b] transition hover:translate-x-1">Tech Stack</NuxtLink>
          <NuxtLink to="/certification" class="text-sm text-[#ff3b3b] font-semibold transition hover:translate-x-1">Certifications</NuxtLink>
        </nav>
      </div>
    </aside>

    <main class="flex-1 p-5 md:p-10 flex justify-center items-center z-10">
      <div class="w-full max-w-[1100px] space-y-6">
    
        <div class="flex items-center justify-between border-b border-[#2a2a2a] pb-4">
          <div>
            <span class="text-xs font-mono text-[#ff3b3b] tracking-wider uppercase">Portfolio // Verified Credentials</span>
            <h1 class="text-3xl md:text-4xl font-extrabold text-white mt-1">Certifications</h1>
          </div>
          <div class="hidden sm:block text-right">
            <span class="inline-block w-2.5 h-2.5 bg-[#ff3b3b] rounded-full animate-pulse mr-2"></span>
            <span class="text-xs text-[#888] font-mono">3 Records</span>
          </div>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
          <div 
            v-for="cert in certifications" 
            :key="cert.title"
            class="rounded-2xl border border-[#2a2a2a] p-6 md:p-8 bg-[#141416]/90 backdrop-blur-sm shadow-xl flex flex-col justify-between hover:border-[#ff3b3b]/50 transition duration-300 group"
          >
            <div>
              <div class="flex items-center justify-between mb-5">
                <span class="px-3 py-1 rounded bg-[#ff3b3b]/10 text-[#ff3b3b] text-xs font-mono border border-[#ff3b3b]/30">
                  {{ cert.issuer }}
                </span>
                <span class="text-xs text-[#888] font-mono tracking-wider">{{ cert.date }}</span>
              </div>

              <div class="w-full aspect-[16/10] rounded-xl bg-[#1a1a1c] border border-[#2a2a2a] p-3 mb-6 flex items-center justify-center overflow-hidden group-hover:border-[#ff3b3b]/40 transition">
                <img 
                  :src="cert.badge" 
                  :alt="cert.title" 
                  class="w-full h-full object-contain rounded transform group-hover:scale-105 transition duration-500"
                  @error="$event.target.src='/images/background/logo.png'"
                />
              </div>

              <h2 class="text-xl font-bold text-white group-hover:text-[#ff3b3b] transition leading-snug mb-1">{{ cert.title }}</h2>
              <span class="text-[11px] text-[#888] font-mono block mb-4">{{ cert.code }}</span>

              <p class="text-xs text-[#bbb] leading-relaxed mb-6">{{ cert.desc }}</p>
            </div>

            <div class="pt-4 border-t border-[#2a2a2a] flex items-center justify-between">
              <span class="text-[11px] text-[#888] font-mono flex items-center gap-1.5">
                <span class="w-1.5 h-1.5 rounded-full bg-[#ff3b3b]"></span> Verified Status
              </span>
              <span class="text-xs font-semibold text-[#ff3b3b] group-hover:translate-x-1 transition flex items-center gap-1 font-mono">
                Active &rarr;
              </span>
            </div>
          </div>
        </div>

      </div>
    </main>

  </div>
</template>