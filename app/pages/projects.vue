<template>
  <div class="max-w-4xl mx-auto px-6 py-16 space-y-8">
    <div>
      <h1 class="text-3xl font-extrabold text-slate-100 mb-2">Featured Projects</h1>
      <p class="text-slate-400">Applications, system architectures, and capstone developments.</p>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
      <!-- UniClaim Card -->
      <div class="p-6 rounded-xl bg-slate-900 border border-slate-800 flex flex-col justify-between space-y-4">
        <div class="space-y-2">
          <div class="flex items-center justify-between">
            <h3 class="text-xl font-bold text-slate-100">UniClaim</h3>
            <span class="text-xs px-2 py-1 rounded bg-red-500/10 text-red-400 border border-red-500/20 font-medium">Web App</span>
          </div>
          <p class="text-sm text-slate-400 leading-relaxed">
            Institutional campus lost and found management system with domain-restricted email authentication, masked detail previews, and blind-challenge verification.
          </p>
        </div>
        <div class="flex flex-wrap gap-2 pt-2">
          <span class="text-xs px-2 py-1 rounded bg-slate-800 text-slate-300">PostgreSQL</span>
          <span class="text-xs px-2 py-1 rounded bg-slate-800 text-slate-300">Nuxt 3</span>
          <span class="text-xs px-2 py-1 rounded bg-slate-800 text-slate-300">Tailwind</span>
        </div>
      </div>

      <!-- LabSync Card -->
      <div class="p-6 rounded-xl bg-slate-900 border border-slate-800 flex flex-col justify-between space-y-4">
        <div class="space-y-2">
          <div class="flex items-center justify-between">
            <h3 class="text-xl font-bold text-slate-100">LabSync</h3>
            <span class="text-xs px-2 py-1 rounded bg-red-500/10 text-red-400 border border-red-500/20 font-medium">PWA</span>
          </div>
          <p class="text-sm text-slate-400 leading-relaxed">
            Offline-first Progressive Web Application built for Medical Laboratory Science departments featuring Service Workers, Tesseract.js OCR, and TF-IDF search.
          </p>
        </div>
        <div class="flex flex-wrap gap-2 pt-2">
          <span class="text-xs px-2 py-1 rounded bg-slate-800 text-slate-300">JavaScript</span>
          <span class="text-xs px-2 py-1 rounded bg-slate-800 text-slate-300">Tesseract.js</span>
          <span class="text-xs px-2 py-1 rounded bg-slate-800 text-slate-300">PWA</span>
        </div>
      </div>
    </div>
  </div>
</template>