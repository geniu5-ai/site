<template>
  <section class="py-10 border-y border-white/[.06] overflow-hidden">
    <p class="text-center text-[11px] text-slate-600 uppercase tracking-[.2em] mb-7 font-medium">
      Todos os canais que seus clientes usam
    </p>

    <!-- Marquee de canais -->
    <div class="flex overflow-hidden" style="mask-image: linear-gradient(90deg, transparent 0%, black 15%, black 85%, transparent 100%);">
      <div class="marquee-track gap-10">
        <div v-for="c in [...channels, ...channels]" :key="`${c.name}-${Math.random()}`" class="flex items-center gap-2.5 shrink-0">
          <div
            class="w-8 h-8 rounded-xl flex items-center justify-center text-sm font-bold"
            :style="`background: ${c.bg}18; color: ${c.color}; border: 1px solid ${c.bg}30;`"
          >
            {{ c.icon }}
          </div>
          <span class="text-slate-400 text-sm font-medium whitespace-nowrap mono">{{ c.name }}</span>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const channels = [
  { name: 'WhatsApp', icon: '💬', bg: '#25d366', color: '#25d366' },
  { name: 'Instagram', icon: '📸', bg: '#e1306c', color: '#e1306c' },
  { name: 'Messenger', icon: '✉️', bg: '#0078ff', color: '#0078ff' },
  { name: 'Telegram', icon: '✈️', bg: '#229ed9', color: '#229ed9' },
  { name: 'Webchat', icon: '🌐', bg: '#a78bfa', color: '#a78bfa' },
  { name: 'E-mail', icon: '@', bg: '#64748b', color: '#94a3b8' },
  { name: 'SMS', icon: '📱', bg: '#f59e0b', color: '#f59e0b' },
]
</script>
