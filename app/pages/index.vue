<template>
  <div class="max-w-4xl mx-auto px-6 py-16">
    <div class="space-y-6">
      <div class="inline-block px-3 py-1 rounded-full bg-red-500/10 text-red-400 text-xs font-semibold tracking-wide border border-red-500/20">
        Information Technology Student & Developer
      </div>
      
      <h1 class="text-4xl sm:text-6xl font-extrabold tracking-tight text-slate-100">
        Hi, I'm <span class="text-red-500">Juliane Cyruz</span>.
      </h1>
      
      <p class="text-lg text-slate-400 max-w-2xl leading-relaxed">
        Building robust full-stack applications, database schemas, and modern web experiences. Passionate about software development, clean design, and continuous learning.
      </p>

      <div class="flex flex-wrap gap-4 pt-4">
        <NuxtLink 
          to="/about" 
          class="px-6 py-3 rounded-lg bg-red-600 hover:bg-red-500 text-white font-medium text-sm transition shadow-lg shadow-red-600/20">
          Explore About Me
        </NuxtLink>
        <NuxtLink 
          to="/certification" 
          class="px-6 py-3 rounded-lg bg-slate-900 hover:bg-slate-800 text-slate-300 font-medium text-sm transition border border-slate-800">
          View Certifications
        </NuxtLink>
      </div>
    </div>
  </div>
</template>