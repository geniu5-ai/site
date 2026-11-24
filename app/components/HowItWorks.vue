<script setup>
const sectionRef = ref(null)

onMounted(async () => {
  const { gsap } = await import('gsap')
  const { ScrollTrigger } = await import('gsap/ScrollTrigger')
  gsap.registerPlugin(ScrollTrigger)

  gsap.fromTo(
    sectionRef.value?.querySelectorAll('.step-card'),
    { y: 44, opacity: 0 },
    {
      y: 0, opacity: 1, duration: .75, stagger: .13, ease: 'power3.out',
      scrollTrigger: { trigger: sectionRef.value, start: 'top 68%' }
    }
  )
})

const steps = [
  {
    num: '01',
    icon: '📩',
    title: 'Mensagem chega',
    desc: 'WhatsApp, Instagram, Messenger — não importa o canal. Tudo converge para um único lugar.',
    color: '#00e87b',
  },
  {
    num: '02',
    icon: '⚡',
    title: 'Genius organiza',
    desc: 'Identifica o cliente, resgata o histórico completo e encaminha para o departamento certo — automaticamente.',
    color: '#0ea5e9',
  },
  {
    num: '03',
    icon: '🤖',
    title: 'IA atende ou escala',
    desc: 'Responde o que pode. Quando precisar de humano, transfere com o contexto todo — sem o cliente repetir nada.',
    color: '#a78bfa',
  },
  {
    num: '04',
    icon: '📈',
    title: 'Você só acompanha',
    desc: 'Filas, tempo de resposta, equipe e performance ficam visíveis. Nada escondido em celular pessoal.',
    color: '#00e87b',
  },
]
</script>

<template>
  <section id="como-funciona" ref="sectionRef" class="py-16 px-6 relative">

    <!-- Grid bg -->
    <div class="absolute inset-0 dot-grid opacity-40 pointer-events-none" />

    <div class="max-w-7xl mx-auto">

      <div class="text-center mb-12">
        <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full border border-emerald-500/30 bg-emerald-500/10 text-emerald-400 text-xs font-semibold mb-6 uppercase tracking-widest">
          Como funciona
        </div>
        <h2 class="display text-white leading-[.95] tracking-tight mb-4" style="font-size: clamp(2rem, 4.5vw, 3.4rem);">
          Uma conversa.<br />
          <span class="g-text">Uma operação inteira.</span>
        </h2>
        <p class="text-slate-400 text-lg max-w-md mx-auto">
          Do primeiro contato ao cliente satisfeito — sem intervenção manual.
        </p>
      </div>

      <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-5">
        <div
          v-for="step in steps"
          :key="step.num"
          class="step-card relative p-6 rounded-2xl g-card group"
        >
          <!-- Number watermark -->
          <div
            class="absolute top-4 right-5 display font-black text-5xl leading-none select-none"
            :style="`color: ${step.color}20;`"
          >
            {{ step.num }}
          </div>

          <!-- Icon -->
          <div
            class="w-11 h-11 rounded-xl flex items-center justify-center text-2xl mb-5 border transition-transform group-hover:scale-105"
            :style="`background: ${step.color}14; border-color: ${step.color}28;`"
          >
            {{ step.icon }}
          </div>

          <!-- Dot connector line (not last) -->
          <div
            v-if="step.num !== '04'"
            class="hidden lg:block absolute top-[46px] -right-3 w-6 h-px"
            :style="`background: linear-gradient(90deg, ${step.color}50, transparent);`"
          />

          <h3 class="display font-bold text-white text-lg mb-2.5">{{ step.title }}</h3>
          <p class="text-slate-400 text-sm leading-relaxed">{{ step.desc }}</p>
        </div>
      </div>
    </div>
  </section>
</template>
