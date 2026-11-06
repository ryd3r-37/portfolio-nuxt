<script setup>
import { ref } from 'vue'

const navOpen = ref(false)

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
      { name: 'GitHub', icon: 'github.png' },
      { name: 'Git', icon: 'git.png' }
    ]
  }
])
</script>

<template>
  <div class="bg-[#0f0f10] text-[#ddd] flex min-h-screen flex-col md:flex-row font-inter transition-colors duration-300 relative overflow-hidden">
    
    <!-- Decorative Glow Accents -->
    <div class="absolute -top-32 -right-32 w-96 h-96 bg-[#ff3b3b]/10 rounded-full blur-3xl pointer-events-none"></div>
    <div class="absolute -bottom-32 -left-32 w-96 h-96 bg-[#ff3b3b]/5 rounded-full blur-3xl pointer-events-none"></div>

    <!-- Sidebar Navigation -->
    <aside class="sticky top-0 h-auto md:h-screen w-full md:w-[240px] bg-[#141416] border-b md:border-b-0 md:border-r border-[#2a2a2a] p-5 flex flex-row md:flex-col justify-between items-center z-50">
      
      <!-- Top Section: Logo -->
      <div class="w-full flex md:flex-col items-center justify-between md:justify-start gap-4">
        <div class="w-full flex items-center justify-between">
          <NuxtLink to="/" class="block transition hover:scale-105 active:scale-95 shrink-0">
            <div class="w-16 h-16 bg-[#2a2a2a] rounded-[14px] flex items-center justify-center border border-[#333] overflow-hidden">
              <img src="/images/background/logo.png" alt="Logo" class="w-full h-full object-cover" />
            </div>
          </NuxtLink>
        </div>

        <!-- Mobile Navigation Toggle Button -->
        <div class="flex items-center gap-3 md:hidden">
          <button @click="navOpen = !navOpen" class="cursor-pointer flex flex-col gap-1.5 p-2 bg-transparent border-none" aria-label="Toggle Navigation Menu">
            <span class="block w-6 h-0.5 bg-[#bbb] transition-all duration-300" :class="{ 'rotate-45 translate-y-2 bg-[#ff3b3b]': navOpen }"></span>
            <span class="block w-6 h-0.5 bg-[#bbb] transition-all duration-300" :class="{ 'opacity-0': navOpen }"></span>
            <span class="block w-6 h-0.5 bg-[#bbb] transition-all duration-300" :class="{ '-rotate-45 -translate-y-2 bg-[#ff3b3b]': navOpen }"></span>
          </button>
        </div>
      </div>

      <!-- Middle Section: Nav Links -->
      <div :class="navOpen ? 'flex' : 'hidden'" class="md:flex flex-col items-center gap-4 w-full my-auto py-6 absolute md:static top-full left-0 bg-[#141416] md:bg-transparent p-5 md:p-0 border-b border-[#2a2a2a] md:border-none z-40">
        <div class="text-xs font-mono uppercase tracking-widest text-[#ff3b3b] font-bold mb-1">Navigation</div>
        <nav class="flex flex-col items-center gap-3 w-full">
          <NuxtLink to="/" class="text-sm font-medium text-[#bbb] hover:text-[#ff3b3b] transition hover:scale-105">Home</NuxtLink>
          <NuxtLink to="/about" class="text-sm font-medium text-[#bbb] hover:text-[#ff3b3b] transition hover:scale-105">About</NuxtLink>
          <NuxtLink to="/techstack" class="text-sm font-semibold text-[#ff3b3b] transition hover:scale-105">Tech Stack</NuxtLink>
          <NuxtLink to="/certification" class="text-sm font-medium text-[#bbb] hover:text-[#ff3b3b] transition hover:scale-105">Certifications</NuxtLink>
        </nav>
      </div>

      <!-- Bottom Section: Social Links -->
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

    <!-- Main Content Area -->
    <main class="flex-1 p-6 md:p-12 overflow-y-auto">
      <div class="max-w-[1200px] mx-auto space-y-8">
        
        <!-- Header Banner -->
        <div class="flex flex-col md:flex-row md:items-center justify-between gap-4 border-b border-[#2a2a2a] pb-6">
          <div>
            <div class="text-xs font-mono uppercase tracking-widest text-[#ff3b3b] font-bold mb-1">Portfolio // Tools & Environment</div>
            <h1 class="text-3xl md:text-4xl font-extrabold text-white tracking-tight">Tech Stack</h1>
          </div>
          <div class="text-xs font-mono text-[#888] bg-[#141416] px-3 py-1.5 rounded-lg border border-[#2a2a2a] w-fit flex items-center gap-2">
            <span class="w-2 h-2 rounded-full bg-[#ff3b3b] animate-pulse"></span>
            Development Ecosystem
          </div>
        </div>

        <!-- Tech Stack Bento Cards -->
        <div class="space-y-6">
          <div 
            v-for="(cat, idx) in techCategories" 
            :key="cat.category"
            class="rounded-2xl border border-[#2a2a2a] bg-[#141416]/90 backdrop-blur-sm p-8 shadow-xl space-y-6"
          >
            <div class="flex items-center gap-3">
              <span class="px-2.5 py-1 rounded-md bg-[#ff3b3b]/10 border border-[#ff3b3b]/20 text-xs font-mono font-bold text-[#ff3b3b]">0{{ idx + 1 }}</span>
              <div>
                <h2 class="text-xl font-bold text-white">{{ cat.category }}</h2>
                <p class="text-xs text-[#888]">{{ cat.desc }}</p>
              </div>
            </div>

            <div class="flex flex-wrap gap-3">
              <div 
                v-for="item in cat.items" 
                :key="item.name"
                class="px-4 py-2.5 rounded-xl bg-[#1a1a1c] border border-[#2a2a2a] flex items-center gap-3 text-xs text-[#ddd] hover:border-[#ff3b3b]/50 hover:text-white transition cursor-default"
              >
                <!-- Tech Icon Image with Fallback -->
                <div class="w-5 h-5 flex items-center justify-center shrink-0">
                  <img 
                    :src="`/images/tech-stack/${item.icon}`" 
                    :alt="item.name" 
                    class="w-full h-full object-contain"
                    @error="$event.target.style.display='none'" 
                  />
                </div>
                <span class="font-medium">{{ item.name }}</span>
              </div>
            </div>
          </div>
        </div>

      </div>
    </main>

  </div>
</template>