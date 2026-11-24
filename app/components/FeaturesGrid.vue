<script setup>
const sectionRef = ref(null)

onMounted(async () => {
  const { gsap } = await import('gsap')
  const { ScrollTrigger } = await import('gsap/ScrollTrigger')
  gsap.registerPlugin(ScrollTrigger)

  gsap.fromTo(sectionRef.value?.querySelectorAll('.feat-card'),
    { y: 50, opacity: 0 },
    {
      y: 0, opacity: 1, duration: .75, stagger: .09, ease: 'power3.out',
      scrollTrigger: { trigger: sectionRef.value, start: 'top 68%' }
    }
  )
})

const features = [
  {
    icon: '🔔',
    tag: 'Inbox unificado',
    title: 'Toda mensagem que chega, chega pra você',
    desc: 'Nenhuma conversa sem resposta. Todos os canais em um único inbox organizado por prioridade e departamento.',
    color: '#00e87b',
  },
  {
    icon: '🏢',
    tag: 'WhatsApp Business',
    title: 'Sua empresa no WhatsApp, do jeito certo',
    desc: 'Número oficial da empresa. Sem celular pessoal de funcionário. Sem perder histórico quando alguém sai.',
    color: '#25d366',
  },
  {
    icon: '🧠',
    tag: 'Memória completa',
    title: 'O cliente nunca precisa repetir tudo de novo',
    desc: 'O histórico completo acompanha cada conversa. Transferência com contexto — sem o cliente recomeçar do zero.',
    color: '#0ea5e9',
  },
  {
    icon: '📋',
    tag: 'Gestão de equipe',
    title: 'Cada pessoa sabe o que precisa fazer',
    desc: 'Filas por departamento, responsáveis definidos, prioridades visíveis. Sua equipe trabalha com clareza.',
    color: '#a78bfa',
  },
  {
    icon: '⚙️',
    tag: 'IA com bom senso',
    title: 'A IA atende o que pode. Chama quem deve.',
    desc: 'Autonomia com controle. O Genius decide quando responder sozinho e quando escalar para o humano certo.',
    color: '#f59e0b',
  },
  {
    icon: '🌐',
    tag: 'Multicanal real',
    title: 'WhatsApp, Instagram e mais — um só lugar',
    desc: 'Todos os canais convergem para uma operação única. Você não precisa de seis apps abertos ao mesmo tempo.',
    color: '#06b6d4',
  },
]
</script>

<template>
  <section id="recursos" ref="sectionRef" class="py-16 px-6 relative">

    <div class="max-w-7xl mx-auto">

      <div class="text-center mb-10">
        <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full border border-emerald-500/30 bg-emerald-500/10 text-emerald-400 text-xs font-semibold mb-6 uppercase tracking-widest">
          Recursos
        </div>
        <h2 class="display text-white leading-[.95] tracking-tight mb-4" style="font-size: clamp(2rem, 4.5vw, 3.2rem);">
          Tudo que sua operação precisa.<br />
          <span class="g-text">Nada que ela não precisa.</span>
        </h2>
        <p class="text-slate-400 text-lg max-w-xl mx-auto">
          Sem burocracia. Sem CRM que exige treinamento. Sem chatbot que irrita.
        </p>
      </div>

      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-5">
        <div
          v-for="f in features"
          :key="f.title"
          class="feat-card group p-7 rounded-2xl g-card cursor-default relative overflow-hidden"
        >
          <!-- Glow accent no hover -->
          <div
            class="absolute inset-0 rounded-2xl opacity-0 group-hover:opacity-100 transition-opacity duration-500 pointer-events-none"
            :style="`background: radial-gradient(circle at 20% 80%, ${f.color}0a 0%, transparent 70%);`"
          />

          <div class="text-[10px] font-bold uppercase tracking-[.2em] mb-4 mono" :style="`color: ${f.color}99;`">
            {{ f.tag }}
          </div>

          <div class="text-3xl mb-4">{{ f.icon }}</div>

          <h3 class="display font-bold text-white text-lg leading-tight mb-3">{{ f.title }}</h3>
          <p class="text-slate-400 text-sm leading-relaxed">{{ f.desc }}</p>

          <!-- Bottom accent line -->
          <div
            class="absolute bottom-0 left-0 right-0 h-px opacity-0 group-hover:opacity-100 transition-opacity"
            :style="`background: linear-gradient(90deg, transparent, ${f.color}50, transparent);`"
          />
        </div>
      </div>
    </div>
  </section>
</template>
