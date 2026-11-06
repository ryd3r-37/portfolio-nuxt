<template>
  <div class="min-h-screen bg-slate-950 text-slate-100 font-sans flex flex-col justify-between">
    <header class="border-b border-slate-800 bg-slate-950/80 backdrop-blur sticky top-0 z-50">
      <nav class="max-w-4xl mx-auto px-6 h-16 flex items-center justify-between">
        <NuxtLink to="/" class="text-xl font-bold tracking-tight text-red-500 hover:text-red-400 transition">
          Portfolio
        </NuxtLink>
        <ul class="flex gap-6 text-sm font-medium text-slate-300">
          <li><NuxtLink to="/" class="hover:text-red-400 transition" active-class="text-red-500 font-semibold">Home</NuxtLink></li>
          <li><NuxtLink to="/about" class="hover:text-red-400 transition" active-class="text-red-500 font-semibold">About</NuxtLink></li>
          <li><NuxtLink to="/techstack" class="hover:text-red-400 transition" active-class="text-red-500 font-semibold">Tech Stack</NuxtLink></li>
          <li><NuxtLink to="/certification" class="hover:text-red-400 transition" active-class="text-red-500 font-semibold">Certifications</NuxtLink></li>
        </ul>
      </nav>
    </header>

    <main class="flex-grow">
      <NuxtPage />
    </main>

    <footer class="border-t border-slate-900 py-6 text-center text-xs text-slate-500">
      &copy; {{ new Date().getFullYear() }} Juliane Cyruz Diaz. All rights reserved.
    </footer>
  </div>
</template>