<script setup>
const scrolled = ref(false)

onMounted(() => {
  window.addEventListener('scroll', () => {
    scrolled.value = window.scrollY > 50
  }, { passive: true })
})

const links = [
  { label: 'Como funciona', to: '#como-funciona' },
  { label: 'Recursos', to: '#recursos' },
  { label: 'CRM Autônomo', to: '#crm' },
  { label: 'Preços', to: '#precos' },
]
</script>

<template>
  <nav
    class="fixed top-0 left-0 right-0 z-50 transition-all duration-300"
    :class="scrolled
      ? 'bg-[#07070f]/85 backdrop-blur-xl border-b border-white/[.06]'
      : 'bg-transparent'"
  >
    <div class="max-w-7xl mx-auto px-6 h-[60px] flex items-center justify-between">

      <!-- Logo -->
      <a href="/" class="flex items-center gap-2.5">
        <div class="w-7 h-7 rounded-lg bg-emerald-500 flex items-center justify-center glow-green">
          <span class="text-black font-black text-xs display">G</span>
        </div>
        <span class="font-bold text-white tracking-tight display" style="font-size:1.05rem;">Genius</span>
      </a>

      <!-- Links -->
      <div class="hidden md:flex items-center gap-7">
        <a
          v-for="l in links"
          :key="l.to"
          :href="l.to"
          class="text-sm text-slate-400 hover:text-white transition-colors"
          style="font-family: var(--font-display);"
        >
          {{ l.label }}
        </a>
      </div>

      <!-- Actions -->
      <div class="flex items-center gap-3">
        <a href="https://app.geniusapp.pro/login" class="hidden md:block text-sm text-slate-500 hover:text-white transition-colors">
          Entrar
        </a>
        <a
          href="https://app.geniusapp.pro/register"
          class="px-4 py-2 rounded-lg bg-emerald-500 hover:bg-emerald-400 text-black font-bold text-sm transition-all hover:scale-[1.03] active:scale-95 display"
        >
          Começar grátis
        </a>
      </div>
    </div>
  </nav>
</template>
