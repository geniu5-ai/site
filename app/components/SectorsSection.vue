<script setup>
const sectionRef = ref(null)

onMounted(async () => {
  const { gsap } = await import('gsap')
  const { ScrollTrigger } = await import('gsap/ScrollTrigger')
  gsap.registerPlugin(ScrollTrigger)

  gsap.fromTo(
    sectionRef.value?.querySelectorAll('.sector-card'),
    { y: 30, opacity: 0 },
    {
      y: 0, opacity: 1, duration: .55, stagger: .07, ease: 'power2.out',
      scrollTrigger: { trigger: sectionRef.value, start: 'top 72%' }
    }
  )
})

const sectors = [
  {
    icon: '🏥',
    label: 'Clínicas e consultórios',
    color: '#00e87b',
    bullets: ['Agenda consultas e retornos', 'Responde dúvidas sobre convênios', 'Lembra pacientes de consultas por WhatsApp'],
  },
  {
    icon: '🦷',
    label: 'Odontologia',
    color: '#0ea5e9',
    bullets: ['Triagem de dor aguda como urgência', 'Apresenta procedimentos e valores', 'Confirma e reduz faltas com lembretes'],
  },
  {
    icon: '⚖️',
    label: 'Advocacia',
    color: '#a78bfa',
    bullets: ['Qualifica área jurídica e urgência', 'Agenda consultas iniciais gratuitas', 'Explica honorários sem expor o advogado'],
  },
  {
    icon: '🏠',
    label: 'Imobiliárias',
    color: '#f59e0b',
    bullets: ['Apresenta imóveis por perfil e budget', 'Agenda visitas automaticamente', 'Acompanha interesse do lead no CRM'],
  },
  {
    icon: '✂️',
    label: 'Estética e beleza',
    color: '#f472b6',
    bullets: ['Agendamento online 24h pelo WhatsApp', 'Divulga promoções e pacotes', 'Dispara lembretes de retorno e aniversário'],
  },
  {
    icon: '🛒',
    label: 'E-commerce',
    color: '#fb923c',
    bullets: ['Rastreia pedidos em tempo real', 'Processa trocas e devoluções', 'Recupera carrinhos abandonados por IA'],
  },
  {
    icon: '🏋️',
    label: 'Academias e studios',
    color: '#34d399',
    bullets: ['Converte visitantes do Instagram em alunos', 'Agenda aulas experimentais', 'Retém alunos com follow-up automático'],
  },
  {
    icon: '🎓',
    label: 'Cursos e educação',
    color: '#60a5fa',
    bullets: ['Tira dúvidas sobre grade e mensalidades', 'Qualifica leads por área de interesse', 'Segue alunos no funil de matrícula'],
  },
]
</script>

<template>
  <section ref="sectionRef" class="py-16 px-6 relative overflow-hidden">

    <div class="absolute inset-0 dot-grid opacity-20 pointer-events-none" />

    <div class="max-w-7xl mx-auto">

      <div class="text-center mb-10">
        <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full border border-white/10 bg-white/4 text-slate-400 text-xs font-semibold mb-6 uppercase tracking-widest">
          Por segmento
        </div>
        <h2 class="display text-white leading-[.95] tracking-tight" style="font-size: clamp(2rem, 4.5vw, 3.4rem);">
          Já configurado para<br />
          <span class="g-text">o seu tipo de negócio.</span>
        </h2>
        <p class="text-slate-400 text-base mt-4 max-w-xl mx-auto">
          O Genius não é um construtor de chatbot que você precisa configurar do zero.
          É um agente comercial pré-treinado para o seu setor.
        </p>
      </div>

      <div class="grid sm:grid-cols-2 lg:grid-cols-4 gap-4">
        <div
          v-for="sector in sectors"
          :key="sector.label"
          class="sector-card g-card p-6 group cursor-default relative overflow-hidden"
        >
          <!-- Glow on hover -->
          <div
            class="absolute inset-0 opacity-0 group-hover:opacity-100 transition-opacity duration-500 pointer-events-none rounded-2xl"
            :style="`background: radial-gradient(circle at 50% 0%, ${sector.color}10 0%, transparent 70%);`"
          />

          <div class="flex items-center gap-3 mb-4">
            <div
              class="w-10 h-10 rounded-xl flex items-center justify-center text-xl border shrink-0"
              :style="`background: ${sector.color}14; border-color: ${sector.color}28;`"
            >
              {{ sector.icon }}
            </div>
            <h3 class="display font-bold text-white text-sm leading-snug">{{ sector.label }}</h3>
          </div>

          <ul class="space-y-2">
            <li
              v-for="bullet in sector.bullets"
              :key="bullet"
              class="flex items-start gap-2 text-slate-400 text-xs leading-relaxed"
            >
              <svg class="w-3 h-3 mt-0.5 shrink-0 transition-colors" :style="`color: ${sector.color};`" fill="currentColor" viewBox="0 0 20 20">
                <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
              </svg>
              {{ bullet }}
            </li>
          </ul>
        </div>
      </div>

      <p class="text-center text-slate-600 text-sm mt-10">
        Não encontrou seu setor?
        <a href="#demo" class="text-emerald-400 hover:text-emerald-300 transition-colors">Fale com a gente</a>
        — o Genius se adapta a qualquer negócio.
      </p>
    </div>
  </section>
</template>
