<script setup>
const sectionRef = ref(null)

onMounted(async () => {
  const { gsap } = await import('gsap')
  const { ScrollTrigger } = await import('gsap/ScrollTrigger')
  gsap.registerPlugin(ScrollTrigger)

  gsap.fromTo(
    sectionRef.value?.querySelectorAll('.step-item'),
    { y: 40, opacity: 0 },
    {
      y: 0, opacity: 1, duration: .7, stagger: .15, ease: 'power3.out',
      scrollTrigger: { trigger: sectionRef.value, start: 'top 72%' }
    }
  )
})

const steps = [
  {
    num: '01',
    title: 'Conecte seus canais',
    desc: 'WhatsApp, Instagram, Messenger e chat do site em minutos. Sem dev, sem código.',
    svg: '<svg class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.7"><path stroke-linecap="round" stroke-linejoin="round" d="M13.828 10.172a4 4 0 00-5.656 0l-4 4a4 4 0 105.656 5.656l1.102-1.101m-.758-4.899a4 4 0 005.656 0l4-4a4 4 0 00-5.656-5.656l-1.1 1.1"/></svg>',
    color: '#00e87b',
  },
  {
    num: '02',
    title: 'Descreva sua empresa',
    desc: 'Serviços, preços, horários, objeções comuns. O agente aprende como você faria — uma vez só.',
    svg: '<svg class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.7"><path stroke-linecap="round" stroke-linejoin="round" d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z"/></svg>',
    color: '#0ea5e9',
  },
  {
    num: '03',
    title: 'A IA começa a vender',
    desc: 'Atende, qualifica, agenda e encaminha leads. 24/7, em todos os canais, sem você gerenciar.',
    svg: '<svg class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.7"><path stroke-linecap="round" stroke-linejoin="round" d="M13 10V3L4 14h7v7l9-11h-7z"/></svg>',
    color: '#a78bfa',
  },
]
</script>

<template>
  <section ref="sectionRef" class="py-14 px-6 relative overflow-hidden">

    <div class="max-w-5xl mx-auto">

      <div class="text-center mb-10">
        <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full border border-white/10 bg-white/4 text-slate-400 text-xs font-semibold mb-6 uppercase tracking-widest">
          Em 3 passos
        </div>
        <h2 class="display text-white leading-[.95] tracking-tight" style="font-size: clamp(1.9rem, 4vw, 3.2rem);">
          Conecte. Explique.<br />
          <span class="g-text">A IA cuida do resto.</span>
        </h2>
        <p class="text-slate-500 text-base mt-4 max-w-md mx-auto">
          Sem contrato de implantação. Sem meses de treinamento. Funciona no dia que você ativa.
        </p>
      </div>

      <div class="grid md:grid-cols-3 gap-6 relative">

        <!-- Connector line (desktop) -->
        <div class="hidden md:block absolute top-[52px] left-[calc(16.67%+1.5rem)] right-[calc(16.67%+1.5rem)] h-px bg-gradient-to-r from-emerald-500/30 via-sky-500/20 to-violet-500/30 pointer-events-none" />

        <div
          v-for="step in steps"
          :key="step.num"
          class="step-item relative p-7 rounded-2xl g-card group"
        >
          <div
            class="absolute top-5 right-6 display font-black text-6xl leading-none select-none"
            :style="`color: ${step.color}12;`"
          >
            {{ step.num }}
          </div>

          <div
            class="w-12 h-12 rounded-xl flex items-center justify-center mb-5 border transition-all group-hover:scale-105"
            :style="`background: ${step.color}14; border-color: ${step.color}28; color: ${step.color};`"
            v-html="step.svg"
          />

          <h3 class="display font-bold text-white text-lg mb-2.5">{{ step.title }}</h3>
          <p class="text-slate-400 text-sm leading-relaxed">{{ step.desc }}</p>

          <div
            class="absolute bottom-0 left-6 right-6 h-px opacity-0 group-hover:opacity-100 transition-opacity duration-300"
            :style="`background: linear-gradient(90deg, transparent, ${step.color}50, transparent);`"
          />
        </div>
      </div>

      <div class="flex items-center justify-center gap-2.5 mt-12 text-slate-600 text-sm">
        <svg class="w-4 h-4 text-emerald-500 shrink-0" fill="currentColor" viewBox="0 0 20 20">
          <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd"/>
        </svg>
        Configuração inicial em menos de 30 minutos — sem nenhuma linha de código
      </div>
    </div>
  </section>
</template>
