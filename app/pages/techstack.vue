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

// Updated with image filename references matching your /public/images/tech-stack/ folder
const techCategories = ref([
  {
    category: 'Databases & Architecture',
    desc: 'Relational schema design, normalization, and SQL query tuning.',
    items: [
      { name: 'PostgreSQL', icon: 'postgre.png' },
      { name: 'MySQL', icon: 'mysql.png' }
    ]
  },
  {
    category: 'Languages & Frameworks',
    desc: 'Building responsive web frontends, desktop utilities, and mobile applications.',
    items: [
      { name: 'Java', icon: 'java.png' },
      { name: 'JavaScript', icon: 'javascript.png' },
      { name: 'Tailwind CSS', icon: 'tailwind.png' },
      { name: 'HTML5', icon: 'html.png' }
    ]
  },
  {
    category: 'Tools & Development Workflow',
    desc: 'IDEs, version control platforms, and database management systems.',
    items: [
      { name: 'VS Code', icon: 'vscode.png' },
      { name: 'Android Studio', icon: 'andstud.png' },
      { name: 'GitHub', icon: 'githubwhite.png' },
      { name: 'Git', icon: 'git.png' }
    ]
  }
])
</script>

<template>
  <div :class="{ 'light-mode': isLightMode }" class="bg-[#0f0f10] text-[#ddd] flex min-h-screen flex-col md:flex-row font-inter transition-colors duration-300">
    
    <!-- Sidebar Navigation -->
    <aside class="sticky top-0 h-auto md:h-screen w-full md:w-[230px] bg-[#141416] border-b md:border-b-0 md:border-r border-[#2a2a2a] p-4 md:p-5 flex flex-row md:flex-col items-center justify-between md:justify-center gap-4 z-50">
      <NuxtLink to="/" class="block transition hover:scale-105 active:scale-95 shrink-0">
        <div class="w-20 h-20 bg-[#2a2a2a] rounded-[14px] flex items-center justify-center border border-[#333] overflow-hidden">
          <img src="/images/background/logo.png" alt="Logo" class="w-full h-full object-cover" />
        </div>
      </NuxtLink>

      <!-- Theme Switcher -->
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
      
      <!-- Mobile Menu Toggle -->
      <button @click="navOpen = !navOpen" class="md:hidden cursor-pointer flex flex-col gap-1.5 p-2 z-50 bg-transparent border-none" aria-label="Toggle Navigation Menu">
        <span class="block w-6 h-0.5 bg-[#bbb] transition-all duration-300" :class="{ 'rotate-45 translate-y-2 bg-[#ff3b3b]': navOpen }"></span>
        <span class="block w-6 h-0.5 bg-[#bbb] transition-all duration-300" :class="{ 'opacity-0': navOpen }"></span>
        <span class="block w-6 h-0.5 bg-[#bbb] transition-all duration-300" :class="{ '-rotate-45 -translate-y-2 bg-[#ff3b3b]': navOpen }"></span>
      </button>
      
      <!-- Nav Links -->
      <div :class="navOpen ? 'flex' : 'hidden'" class="md:flex flex-col items-center gap-4 absolute md:static top-full left-0 w-full bg-[#141416] md:bg-transparent p-5 md:p-0 border-b border-[#2a2a2a] md:border-none z-40">
        <div class="text-base font-bold text-[#ff3b3b] hidden md:block">Menu</div>
        <nav class="flex flex-col items-center gap-3 md:gap-2">
          <NuxtLink to="/" class="text-sm text-[#bbb] hover:text-[#ff3b3b] transition hover:translate-x-1">Home</NuxtLink>
          <NuxtLink to="/about" class="text-sm text-[#bbb] hover:text-[#ff3b3b] transition hover:translate-x-1">About</NuxtLink>
          <NuxtLink to="/techstack" class="text-sm text-[#ff3b3b] font-semibold transition hover:translate-x-1">Tech Stack</NuxtLink>
          <NuxtLink to="/certification" class="text-sm text-[#bbb] hover:text-[#ff3b3b] transition hover:translate-x-1">Certifications</NuxtLink>
        </nav>
      </div>
    </aside>

    <!-- Main Content Area -->
    <main class="flex-1 p-5 md:p-10 flex justify-center items-center">
      <div class="w-full max-w-[950px] space-y-6">
        
        <!-- Header Banner -->
        <div class="flex items-center justify-between border-b border-[#2a2a2a] pb-4">
          <div>
            <span class="text-xs font-mono text-[#ff3b3b] tracking-wider uppercase">Portfolio // Tools & Environment</span>
            <h1 class="text-3xl md:text-4xl font-extrabold text-white mt-1">Tech Stack</h1>
          </div>
          <div class="hidden sm:block text-right">
            <span class="inline-block w-2.5 h-2.5 bg-[#ff3b3b] rounded-full animate-pulse mr-2"></span>
            <span class="text-xs text-[#888] font-mono">Development Ecosystem</span>
          </div>
        </div>

        <!-- Tech Stack Bento Grid with Icons -->
        <div class="space-y-6">
          <section 
            v-for="(cat, idx) in techCategories" 
            :key="cat.category"
            class="rounded-2xl border border-[#2a2a2a] p-6 bg-[#141416] shadow-xl"
          >
            <div class="flex items-center gap-3 mb-2">
              <span class="px-2.5 py-0.5 rounded bg-[#ff3b3b]/10 text-[#ff3b3b] text-xs font-mono border border-[#ff3b3b]/30">0{{ idx + 1 }}</span>
              <h2 class="text-xl font-bold text-white tracking-wide">{{ cat.category }}</h2>
            </div>
            <p class="text-xs text-[#888] mb-5 pl-11">{{ cat.desc }}</p>

            <div class="flex flex-wrap gap-3 pl-0 md:pl-11">
              <div 
                v-for="item in cat.items" 
                :key="item.name"
                class="px-4 py-2.5 rounded-xl bg-[#1a1a1c] border border-[#2a2a2a] text-sm text-[#ddd] font-mono hover:border-[#ff3b3b]/50 hover:text-white transition cursor-default flex items-center gap-3"
              >
                <!-- Tech Icon Image -->
                <div class="w-6 h-6 flex items-center justify-center bg-[#2a2a2a]/50 rounded-md overflow-hidden p-0.5">
                  <img 
                    :src="`/images/tech-stack/${item.icon}`" 
                    :alt="item.name" 
                    class="w-full h-full object-contain"
                    @error="$event.target.style.display='none'" 
                  />
                </div>
                <span>{{ item.name }}</span>
              </div>
            </div>
          </section>
        </div>

      </div>
    </main>

  </div>
</template>