<template>
  <div class="max-w-4xl mx-auto px-6 py-16 space-y-10">
    <div>
      <h1 class="text-3xl font-extrabold text-slate-100 mb-2">Tech Stack</h1>
      <p class="text-slate-400 leading-relaxed">
        Technologies, tools, and platforms I work with for data analytics, database management, and web development.
      </p>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
      <div class="p-6 rounded-xl bg-slate-900 border border-slate-800 space-y-4">
        <h3 class="text-lg font-bold text-red-400">Data & Database Management</h3>
        <ul class="space-y-2 text-sm text-slate-300">
          <li class="flex items-center gap-2"><span class="h-1.5 w-1.5 rounded-full bg-red-400"></span>PostgreSQL & MS SQL Server</li>
          <li class="flex items-center gap-2"><span class="h-1.5 w-1.5 rounded-full bg-red-400"></span>Relational Schema Optimization & ERD Design</li>
          <li class="flex items-center gap-2"><span class="h-1.5 w-1.5 rounded-full bg-red-400"></span>SQL Query Development & Data Extraction</li>
          <li class="flex items-center gap-2"><span class="h-1.5 w-1.5 rounded-full bg-red-400"></span>pgAdmin 4</li>
        </ul>
      </div>

      <div class="p-6 rounded-xl bg-slate-900 border border-slate-800 space-y-4">
        <h3 class="text-lg font-bold text-red-400">Web & Mobile Development</h3>
        <ul class="space-y-2 text-sm text-slate-300">
          <li class="flex items-center gap-2"><span class="h-1.5 w-1.5 rounded-full bg-red-400"></span>Nuxt 3 & Vue.js</li>
          <li class="flex items-center gap-2"><span class="h-1.5 w-1.5 rounded-full bg-red-400"></span>Tailwind CSS, HTML5, CSS3</li>
          <li class="flex items-center gap-2"><span class="h-1.5 w-1.5 rounded-full bg-red-400"></span>JavaScript & Node.js</li>
          <li class="flex items-center gap-2"><span class="h-1.5 w-1.5 rounded-full bg-red-400"></span>Java Swing & Android Studio</li>
        </ul>
      </div>

      <div class="p-6 rounded-xl bg-slate-900 border border-slate-800 space-y-4 md:col-span-2">
        <h3 class="text-lg font-bold text-red-400">Tools & Environment</h3>
        <div class="flex flex-wrap gap-2">
          <span class="px-3 py-1 text-xs rounded-md bg-slate-800 text-slate-300 border border-slate-700">VS Code</span>
          <span class="px-3 py-1 text-xs rounded-md bg-slate-800 text-slate-300 border border-slate-700">Git & GitHub</span>
          <span class="px-3 py-1 text-xs rounded-md bg-slate-800 text-slate-300 border border-slate-700">NetBeans</span>
          <span class="px-3 py-1 text-xs rounded-md bg-slate-800 text-slate-300 border border-slate-700">pgAdmin 4</span>
          <span class="px-3 py-1 text-xs rounded-md bg-slate-800 text-slate-300 border border-slate-700">Android Studio</span>
        </div>
      </div>
    </div>
  </div>
</template>