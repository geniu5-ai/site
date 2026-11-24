<script setup>
const sectionRef = ref(null)

onMounted(async () => {
  const { gsap } = await import('gsap')
  const { ScrollTrigger } = await import('gsap/ScrollTrigger')
  gsap.registerPlugin(ScrollTrigger)

  gsap.fromTo(
    sectionRef.value?.querySelectorAll('.compare-row'),
    { opacity: 0, x: -20 },
    {
      opacity: 1, x: 0, duration: .6, stagger: .09, ease: 'power2.out',
      scrollTrigger: { trigger: sectionRef.value, start: 'top 70%' }
    }
  )
})

const comparisons = [
  { bad: 'Perde o contexto quando chama um humano', good: 'Preserva todo histórico em qualquer transferência' },
  { bad: 'Responde igual para todo mundo', good: 'Adapta a resposta ao perfil e histórico do cliente' },
  { bad: 'Não sabe quando parar de responder', good: 'Sabe exatamente quando escalar para um humano' },
  { bad: 'Instalado em paralelo à operação', good: 'É a operação — com IA dentro' },
  { bad: 'Sem auditoria, sem responsável', good: 'Trilha completa: quem fez o quê e quando' },
]
</script>

<template>
  <section ref="sectionRef" class="py-16 px-6 relative overflow-hidden">

    <div class="absolute inset-0 bg-gradient-to-br from-[#07070f] via-[#0a0814] to-[#07070f]" />
    <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[600px] h-[400px] bg-violet-500/5 rounded-full blur-3xl pointer-events-none" />

    <div class="relative max-w-5xl mx-auto">

      <!-- Header -->
      <div class="text-center mb-10">
        <div class="inline-block px-4 py-1.5 rounded-full border border-violet-500/30 bg-violet-500/8 text-violet-300 text-xs font-semibold mb-6 uppercase tracking-widest">
          O diferencial real
        </div>
        <h2 class="display text-white leading-[.95] tracking-tight" style="font-size: clamp(2.2rem, 5vw, 3.8rem);">
          Não é mais um chatbot.<br />
          <span class="g-text">É outra categoria.</span>
        </h2>
        <p class="text-slate-400 text-lg mt-5 max-w-2xl mx-auto">
          Outras plataformas entregam um construtor de chatbot — você ainda precisa configurar tudo do zero.
          O Genius entrega um <strong class="text-white font-semibold">agente comercial já treinado para o seu tipo de negócio</strong>.
        </p>
      </div>

      <!-- Comparison table -->
      <div class="rounded-2xl overflow-hidden border border-white/7">

        <!-- Header row -->
        <div class="grid grid-cols-2 text-xs font-bold uppercase tracking-widest">
          <div class="py-3 px-6 bg-red-500/8 text-red-400 border-b border-white/7 flex items-center gap-2">
            <span>✗</span> Chatbot tradicional
          </div>
          <div class="py-3 px-6 bg-emerald-500/8 text-emerald-400 border-b border-white/7 border-l border-white/7 flex items-center gap-2">
            <span>✓</span> Genius
          </div>
        </div>

        <!-- Comparison rows -->
        <div
          v-for="(c, i) in comparisons"
          :key="i"
          class="compare-row grid grid-cols-2 border-b border-white/5 last:border-0"
        >
          <div class="py-4 px-6 flex items-start gap-3 bg-red-500/4 hover:bg-red-500/6 transition-colors">
            <span class="text-red-500/60 text-base mt-px shrink-0">✗</span>
            <p class="text-slate-400 text-sm leading-relaxed">{{ c.bad }}</p>
          </div>
          <div class="py-4 px-6 flex items-start gap-3 border-l border-white/5 bg-emerald-500/4 hover:bg-emerald-500/6 transition-colors">
            <span class="text-emerald-400 text-base mt-px shrink-0">✓</span>
            <p class="text-slate-200 text-sm leading-relaxed">{{ c.good }}</p>
          </div>
        </div>
      </div>

      <!-- Tagline -->
      <p class="text-center text-slate-500 text-sm mt-8 italic">
        "O Genius organiza primeiro. A IA trabalha dentro da operação, não fora dela."
      </p>

      <!-- CTA -->
      <div class="flex justify-center mt-10">
        <a
          href="#demo"
          class="group px-6 py-3 rounded-xl bg-emerald-500 hover:bg-emerald-400 text-black font-bold text-sm transition-all hover:scale-[1.04] glow-green flex items-center gap-2 display"
        >
          Ver o agente em ação
          <svg class="w-4 h-4 group-hover:translate-x-1 transition-transform" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
            <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3"/>
          </svg>
        </a>
      </div>
    </div>
  </section>
</template>
