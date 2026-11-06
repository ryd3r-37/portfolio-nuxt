<template>
  <div class="min-h-screen bg-slate-950 text-slate-100 flex flex-col">
    <nav class="flex justify-between items-center px-8 py-4 border-b border-slate-800">
      <div class="font-bold text-lg tracking-wide text-red-500">Portfolio</div>
      <ul class="flex gap-6 text-sm font-medium">
  <li><NuxtLink to="/" class="hover:text-red-400 transition">Home</NuxtLink></li>
  <li><NuxtLink to="/about" class="hover:text-red-400 transition">About</NuxtLink></li>
  <li><NuxtLink to="/projects" class="hover:text-red-400 transition">Projects</NuxtLink></li>
  <li><NuxtLink to="/certification" class="hover:text-red-400 transition">Certifications</NuxtLink></li>
</ul>
    </nav>

    
    <main class="flex-grow">
      <NuxtPage />
    </main>

    
    <footer class="py-6 text-center text-xs text-slate-500 border-t border-slate-800">
      <p>&copy; 2026 Portfolio. All rights reserved.</p>
    </footer>
  </div>
</template>