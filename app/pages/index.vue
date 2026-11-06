<script setup>
import { ref, onMounted } from 'vue'

const isLightMode = ref(false)
const navOpen = ref(false)

onMounted(() => {
  if (localStorage.getItem('theme') === 'light') {
    isLightMode.value = true
    document.documentElement.classList.add('light-mode')
  }
})

const toggleTheme = () => {
  isLightMode.value = !isLightMode.value
  if (isLightMode.value) {
    localStorage.setItem('theme', 'light')
    document.documentElement.classList.add('light-mode')
  } else {
    localStorage.setItem('theme', 'dark')
    document.documentElement.classList.remove('light-mode')
  }
}
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
      
      <button @click="navOpen = !navOpen" class="md:hidden cursor-pointer flex flex-col gap-1.5 p-2 z-50 bg-transparent border-none">
        <span class="block w-6 h-0.5 bg-[#bbb] transition-all duration-300" :class="{ 'rotate-45 translate-y-2 bg-[#ff3b3b]': navOpen }"></span>
        <span class="block w-6 h-0.5 bg-[#bbb] transition-all duration-300" :class="{ 'opacity-0': navOpen }"></span>
        <span class="block w-6 h-0.5 bg-[#bbb] transition-all duration-300" :class="{ '-rotate-45 -translate-y-2 bg-[#ff3b3b]': navOpen }"></span>
      </button>
       
      <div :class="navOpen ? 'flex' : 'hidden'" class="md:flex flex-col items-center gap-4 absolute md:static top-full left-0 w-full bg-[#141416] md:bg-transparent p-5 md:p-0 border-b border-[#2a2a2a] md:border-none z-40">
        <div class="text-base font-bold text-[#ff3b3b] hidden md:block">Menu</div>
        <nav class="flex flex-col items-center gap-3 md:gap-2">
          <NuxtLink to="/" class="text-sm text-[#ff3b3b] font-semibold transition hover:translate-x-1">Home</NuxtLink>
          <NuxtLink to="/about" class="text-sm text-[#bbb] hover:text-[#ff3b3b] transition hover:translate-x-1">About</NuxtLink>
          <NuxtLink to="/techstack" class="text-sm text-[#bbb] hover:text-[#ff3b3b] transition hover:translate-x-1">Tech Stack</NuxtLink>
          <NuxtLink to="/certification" class="text-sm text-[#bbb] hover:text-[#ff3b3b] transition hover:translate-x-1">Certifications</NuxtLink>
        </nav>
      </div>
    </aside>
  
    <main class="flex-1 flex items-center justify-center p-5 md:p-10">
      <div class="w-full max-w-[850px] rounded-[18px] border border-[#2a2a2a] p-8 md:p-12 bg-[#141416] shadow-2xl flex flex-col md:flex-row items-center gap-8">
        <div class="w-40 h-40 md:w-52 md:h-52 rounded-2xl overflow-hidden border-2 border-[#ff3b3b] shrink-0 shadow-lg">
          <img src="/images/personal/Jisi.jpg" alt="Juliane Cyruz Diaz" class="w-full h-full object-cover" />
        </div>
        <div class="text-center md:text-left flex-1">
          <h1 class="text-3xl md:text-4xl font-extrabold text-white mb-2">
            Hi, I'm <span class="text-[#ff3b3b]">Juliane Cyruz Diaz</span>
          </h1>
          <p class="text-sm md:text-base text-[#bbb] mb-6">
            Information Technology student and developer specializing in database management, web applications, and modern UI design.
          </p>
          <div class="flex flex-wrap justify-center md:justify-start gap-4">
            <NuxtLink to="/techstack" class="px-6 py-2.5 bg-[#ff3b3b] text-white font-semibold rounded-lg hover:bg-[#d32f2f] transition">
              View Tech Stack
            </NuxtLink>
            <NuxtLink to="/certification" class="px-6 py-2.5 border border-[#333] bg-[#1a1a1c] text-[#ddd] font-semibold rounded-lg hover:border-[#ff3b3b] transition">
              View Certifications
            </NuxtLink>
          </div>
        </div>
      </div>
    </main>

  </div>
</template>