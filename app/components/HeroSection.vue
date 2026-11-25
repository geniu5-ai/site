<script setup>
const titleRef  = ref(null)
const subRef    = ref(null)
const ctasRef   = ref(null)
const trustRef  = ref(null)
const statsRef  = ref(null)

const bubbles = ref([])
const allBubbles = [
  { channel: 'WhatsApp', color: '#25d366', icon: '💬', text: 'Oi, quero saber o preço do plano Pro', delay: 0 },
  { channel: 'Instagram', color: '#e1306c', icon: '📸', text: 'Vi no feed e me interessei! Como funciona?', delay: 1.6 },
  { channel: 'Messenger', color: '#0078ff', icon: '✉️', text: 'Preciso de um orçamento urgente', delay: 3.2 },
  { channel: 'WhatsApp', color: '#25d366', icon: '💬', text: 'Quando posso agendar uma demo?', delay: 4.8 },
  { channel: 'Telegram', color: '#229ed9', icon: '✈️', text: 'Vocês atendem empresa de 50 pessoas?', delay: 6.4 },
]

const stats = [
  { value: '24/7', label: 'sempre ativo' },
  { value: '0',   label: 'mensagens perdidas' },
  { value: '1',   label: 'lugar pra tudo' },
  { value: '100%',label: 'sem celular pessoal' },
]

onMounted(async () => {
  const { gsap } = await import('gsap')

  const tl = gsap.timeline({ delay: .25 })
  tl.fromTo(titleRef.value,
    { y: 60, opacity: 0 },
    { y: 0, opacity: 1, duration: 1.1, ease: 'power3.out' }
  )
  .fromTo(subRef.value,
    { y: 30, opacity: 0 },
    { y: 0, opacity: 1, duration: .9, ease: 'power3.out' }, '-=.65'
  )
  .fromTo(ctasRef.value,
    { y: 22, opacity: 0 },
    { y: 0, opacity: 1, duration: .7, ease: 'power3.out' }, '-=.5'
  )
  .fromTo(trustRef.value,
    { opacity: 0 },
    { opacity: 1, duration: .5, ease: 'power2.out' }, '-=.3'
  )
  .fromTo(statsRef.value?.querySelectorAll('.stat-item'),
    { y: 16, opacity: 0 },
    { y: 0, opacity: 1, duration: .5, stagger: .08, ease: 'power2.out' }, '-=.3'
  )

  // spawn bubbles periodically
  spawnBubble()
  setInterval(spawnBubble, 2200)
})

let bubbleId = 0
function spawnBubble() {
  const idx = bubbleId % allBubbles.length
  bubbles.value.push({ ...allBubbles[idx], id: bubbleId, active: true })
  bubbleId++
  setTimeout(() => {
    bubbles.value.shift()
  }, 4200)
}
</script>

<template>
  <section class="relative w-full min-h-screen flex items-center justify-center overflow-hidden">

    <!-- Vídeo fullscreen: zoom out via scale, puxado pra cima sangrando borda -->
    <video
      class="absolute w-full object-cover"
      autoplay muted loop playsinline
      style="top: 50%; left: 50%; width: 130%; height: 100%; transform: translate(-50%, -50%); object-position: center center;"
    >
      <source src="/hero-video.mp4" type="video/mp4" />
    </video>

    <!-- Overlay de escurecimento sobre o vídeo (sem cobrir o vídeo com gradiente sólido) -->
    <div class="hero-overlay absolute inset-0" />

    <!-- Conteúdo centralizado -->
    <div class="relative z-10 flex flex-col items-center text-center px-6 w-full max-w-4xl mx-auto">


      <!-- Headline menor e mais elegante -->
      <h1
        ref="titleRef"
        class="display leading-[.96] tracking-tight mb-5 w-full"
        style="font-size: clamp(2.4rem, 5.5vw, 4.6rem); opacity:0; text-shadow: 0 4px 40px rgba(0,0,0,.8);"
      >
        <span class="text-white">Seu negócio vende.</span><br />
        <span class="g-text">O Genius cuida do resto.</span>
      </h1>

      <!-- Sub -->
      <p
        ref="subRef"
        class="text-slate-200/85 mb-8 leading-relaxed max-w-xl w-full"
        style="font-size: clamp(1rem, 1.8vw, 1.15rem); opacity:0; font-weight:300; text-shadow: 0 2px 20px rgba(0,0,0,.9);"
      >
        Uma inteligência que atende, organiza e converte — em todos os seus canais,
        <em class="not-italic text-emerald-300 font-medium">sem você gerenciar nada.</em>
      </p>

      <!-- CTAs -->
      <div ref="ctasRef" class="flex flex-col sm:flex-row items-center justify-center gap-4 mb-8 w-full" style="opacity:0;">
        <a
          href="https://app.geniusapp.pro/register"
          class="group px-7 py-3.5 rounded-xl bg-emerald-500 hover:bg-emerald-400 text-black font-bold text-sm transition-all hover:scale-[1.04] active:scale-95 glow-green flex items-center gap-2.5 display"
        >
          Começar grátis
          <svg class="w-4 h-4 group-hover:translate-x-1 transition-transform" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
            <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3"/>
          </svg>
        </a>
        <a
          href="#demo"
          class="px-7 py-3.5 rounded-xl border border-white/18 hover:border-white/35 text-white font-semibold text-sm transition-all hover:bg-white/7 backdrop-blur-sm flex items-center gap-2"
        >
          <svg class="w-4 h-4 text-emerald-400" fill="currentColor" viewBox="0 0 24 24">
            <path d="M8 5v14l11-7z"/>
          </svg>
          Ver demonstração
        </a>
      </div>

      <!-- Trust line -->
      <p class="text-slate-500/70 text-xs mb-10 tracking-wide" style="opacity:0;" ref="trustRef">
        Sem dev. Sem código. Começa em minutos.
      </p>

      <!-- Stats -->
      <div ref="statsRef" class="flex flex-wrap items-center justify-center gap-8 sm:gap-10 w-full">
        <div v-for="s in stats" :key="s.label" class="stat-item text-center" style="opacity:0;">
          <div class="text-xl font-black text-emerald-400 display">{{ s.value }}</div>
          <div class="text-xs text-slate-500 mt-0.5 uppercase tracking-widest">{{ s.label }}</div>
        </div>
      </div>
    </div>

    <!-- Bolhas de mensagem flutuantes -->
    <div class="absolute bottom-32 right-8 md:right-20 z-20 flex flex-col gap-3 items-end max-w-xs pointer-events-none">
      <TransitionGroup name="bubble-anim">
        <div
          v-for="b in bubbles.slice(-3)"
          :key="b.id"
          class="flex items-start gap-2 px-3 py-2 rounded-2xl backdrop-blur-md border border-white/10 bg-[#07070f]/70"
        >
          <div
            class="w-6 h-6 rounded-full shrink-0 flex items-center justify-center text-xs"
            :style="`background: ${b.color}22; color: ${b.color};`"
          >
            {{ b.icon }}
          </div>
          <div>
            <div class="text-white/50 text-[10px] mono mb-0.5">{{ b.channel }}</div>
            <div class="text-white/85 text-xs leading-snug">{{ b.text }}</div>
          </div>
        </div>
      </TransitionGroup>
    </div>

    <!-- Scroll indicator -->
    <div class="absolute bottom-8 left-1/2 -translate-x-1/2 text-slate-600 animate-bounce">
      <svg class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M19 9l-7 7-7-7"/>
      </svg>
    </div>
  </section>
</template>

<style scoped>
.bubble-anim-enter-active { animation: float-up .5s ease forwards; }
.bubble-anim-leave-active { animation: float-up .4s ease reverse forwards; }
@keyframes float-up {
  from { opacity:0; transform: translateY(16px) scale(.94); }
  to   { opacity:1; transform: translateY(0)    scale(1);   }
}
</style>
