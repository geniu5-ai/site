<script setup>
const sectionRef = ref(null)

onMounted(async () => {
  const { gsap } = await import('gsap')
  const { ScrollTrigger } = await import('gsap/ScrollTrigger')
  gsap.registerPlugin(ScrollTrigger)

  gsap.fromTo(sectionRef.value,
    { opacity: 0, y: 28 },
    {
      opacity: 1, y: 0, duration: 1, ease: 'power3.out',
      scrollTrigger: { trigger: sectionRef.value, start: 'top 80%' }
    }
  )
})
</script>

<template>
  <section id="demo" ref="sectionRef" class="py-16 px-6 relative overflow-hidden">

    <div class="absolute inset-0">
      <div class="absolute inset-0 bg-gradient-to-br from-emerald-950/45 via-[#07070f] to-blue-950/35" />
      <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[800px] h-[450px] bg-emerald-500/10 rounded-full blur-3xl" />
      <div class="absolute inset-0 dot-grid opacity-20 pointer-events-none" />
    </div>

    <div class="relative max-w-3xl mx-auto text-center">

      <div class="inline-flex items-center gap-2 px-3 py-1.5 rounded-full border border-emerald-500/35 bg-emerald-500/10 text-emerald-400 text-xs font-semibold mb-8 uppercase tracking-widest">
        <span class="w-1.5 h-1.5 rounded-full bg-emerald-400 pulse-dot" />
        Sem cartão de crédito
      </div>

      <h2
        class="display text-white leading-[.93] tracking-tight mb-6"
        style="font-size: clamp(2.6rem, 6.5vw, 5.5rem);"
      >
        Pronto para parar de<br />
        <span class="g-text">perder vendas?</span>
      </h2>

      <p class="text-slate-300 text-xl leading-relaxed mb-12 max-w-lg mx-auto" style="font-weight:300;">
        Configure em minutos. Sem dev, sem TI, sem burocracia.
        Seu atendimento começa a vender por você hoje.
      </p>

      <div class="flex flex-col sm:flex-row items-center justify-center gap-4 mb-10">
        <a
          href="#"
          class="group w-full sm:w-auto px-10 py-5 rounded-xl bg-emerald-500 hover:bg-emerald-400 text-black font-extrabold text-lg transition-all hover:scale-[1.04] active:scale-95 glow-green flex items-center justify-center gap-3 display"
        >
          Criar minha conta grátis
          <svg class="w-5 h-5 group-hover:translate-x-1 transition-transform" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
            <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3"/>
          </svg>
        </a>
        <a
          href="#"
          class="w-full sm:w-auto px-10 py-5 rounded-xl border border-white/15 hover:border-white/30 text-white font-semibold text-lg transition-all hover:bg-white/5"
        >
          Falar com especialista
        </a>
      </div>

      <div class="flex flex-wrap items-center justify-center gap-6 text-slate-500 text-sm">
        <div class="flex items-center gap-2"><span class="text-emerald-500 font-bold">✓</span> Sem cartão de crédito</div>
        <div class="flex items-center gap-2"><span class="text-emerald-500 font-bold">✓</span> Setup em menos de 10 min</div>
        <div class="flex items-center gap-2"><span class="text-emerald-500 font-bold">✓</span> Cancele quando quiser</div>
      </div>
    </div>
  </section>
</template>
