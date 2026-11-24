<script setup>
const sectionRef = ref(null)

onMounted(async () => {
  const { gsap } = await import('gsap')
  const { ScrollTrigger } = await import('gsap/ScrollTrigger')
  gsap.registerPlugin(ScrollTrigger)

  gsap.fromTo(sectionRef.value?.querySelectorAll('.stat-card'),
    { scale: .85, opacity: 0 },
    {
      scale: 1, opacity: 1, duration: .7, stagger: .1, ease: 'back.out(1.5)',
      scrollTrigger: { trigger: sectionRef.value, start: 'top 72%' }
    }
  )
  gsap.fromTo(sectionRef.value?.querySelectorAll('.testi-card'),
    { y: 30, opacity: 0 },
    {
      y: 0, opacity: 1, duration: .7, stagger: .12, ease: 'power3.out',
      scrollTrigger: { trigger: sectionRef.value, start: 'top 65%' }
    }
  )
})

const stats = [
  { value: '10k+',  label: 'conversas por dia',     sub: 'nas empresas ativas' },
  { value: '98%',   label: 'satisfação',              sub: 'NPS médio das operações' },
  { value: '3x',    label: 'mais rápido',             sub: 'no primeiro atendimento' },
  { value: 'zero',  label: 'mensagens sem resposta',  sub: 'com IA ativa 24/7' },
]

const testimonials = [
  {
    quote: 'Antes usávamos 3 celulares para atendimento. Hoje tudo está em um só lugar e consigo acompanhar tudo em tempo real.',
    author: 'Dra. Maria Eduarda',
    role: 'Clínica Médica — São Paulo',
    avatar: 'ME',
  },
  {
    quote: 'O Genius qualificou 3× mais leads do que minha equipe conseguia manualmente. Mudou completamente o processo de vendas.',
    author: 'Rafael Camargo',
    role: 'E-commerce — Rio de Janeiro',
    avatar: 'RC',
  },
  {
    quote: 'Minha equipe agora foca em vender. Toda a burocracia de atendimento, a IA resolve sozinha.',
    author: 'Fernanda Lima',
    role: 'Consultoria — Brasília',
    avatar: 'FL',
  },
]
</script>

<template>
  <section ref="sectionRef" class="py-16 px-6 relative">

    <div class="max-w-7xl mx-auto">

      <!-- Stats -->
      <div class="grid grid-cols-2 md:grid-cols-4 gap-5 mb-24">
        <div
          v-for="s in stats"
          :key="s.label"
          class="stat-card text-center p-7 rounded-2xl g-card"
        >
          <div class="display font-black g-text mb-2" style="font-size:2.5rem; line-height:1;">{{ s.value }}</div>
          <div class="text-white font-semibold text-sm mb-1">{{ s.label }}</div>
          <div class="text-slate-600 text-xs">{{ s.sub }}</div>
        </div>
      </div>

      <!-- Testimonials -->
      <div class="text-center mb-10">
        <span class="text-[11px] text-slate-600 uppercase tracking-[.2em] font-medium">o que dizem quem já usa</span>
      </div>

      <div class="grid md:grid-cols-3 gap-5">
        <div
          v-for="t in testimonials"
          :key="t.author"
          class="testi-card p-7 rounded-2xl g-card"
        >
          <div class="text-emerald-500/25 text-6xl display font-black leading-none mb-4 select-none">"</div>
          <p class="text-slate-300 text-sm leading-relaxed mb-6 italic">{{ t.quote }}</p>
          <div class="flex items-center gap-3">
            <div class="w-9 h-9 rounded-full bg-emerald-500/15 border border-emerald-500/25 flex items-center justify-center text-xs font-bold text-emerald-400 display shrink-0">
              {{ t.avatar }}
            </div>
            <div>
              <div class="text-white font-semibold text-sm">{{ t.author }}</div>
              <div class="text-slate-600 text-xs mt-0.5">{{ t.role }}</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
