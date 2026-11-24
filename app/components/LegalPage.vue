<script setup>
defineProps({
  title: { type: String, required: true },
  updated: { type: String, required: true }
})
</script>

<template>
  <main>
    <header class="border-b border-white/[.06]">
      <div class="max-w-3xl mx-auto px-6 h-[60px] flex items-center justify-between">
        <NuxtLink to="/" class="flex items-center gap-2.5">
          <span class="w-7 h-7 rounded-lg bg-emerald-500 flex items-center justify-center">
            <span class="text-black font-black text-xs display">G</span>
          </span>
          <span class="display font-bold text-white">Genius</span>
        </NuxtLink>
        <NuxtLink to="/" class="text-slate-400 text-sm hover:text-white transition-colors">← Voltar ao site</NuxtLink>
      </div>
    </header>

    <article class="max-w-3xl mx-auto px-6 py-16 legal">
      <h1 class="display text-white text-4xl mb-2">{{ title }}</h1>
      <p class="text-slate-500 text-sm mb-12 mono">Última atualização: {{ updated }}</p>
      <slot />
    </article>

    <TheFooter />
  </main>
</template>

<style scoped>
.legal :deep(h2) { color: #fff; font-weight: 700; font-size: 1.25rem; margin: 2.5rem 0 .75rem; }
.legal :deep(p), .legal :deep(li) { color: #94a3b8; line-height: 1.75; font-size: .95rem; }
.legal :deep(p) { margin-bottom: 1rem; }
.legal :deep(ul) { list-style: disc; padding-left: 1.25rem; margin-bottom: 1rem; }
.legal :deep(a) { color: #34d399; text-decoration: underline; }
.legal :deep(strong) { color: #e2e8f0; }
</style>
