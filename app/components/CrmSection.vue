<script setup>
const sectionRef = ref(null)
const counterEl  = ref(null)

const crmLeads = [
  { initials: 'MC', name: 'Maria Campos',  action: 'Genius enviou proposta',  status: 'Aguardando', color: '#f59e0b' },
  { initials: 'RP', name: 'Rafael Pinto',  action: 'Follow-up automático',    status: 'Respondeu',  color: '#00e87b' },
  { initials: 'AS', name: 'Ana Silva',     action: 'Lead qualificado pela IA', status: '🔥 Quente',  color: '#f87171' },
  { initials: 'JL', name: 'João Lima',     action: 'Reativação enviada',      status: 'Reativado',  color: '#0ea5e9' },
]

const capabilities = [
  { icon: '🎯', text: 'Qualifica leads automaticamente antes de chegar no vendedor' },
  { icon: '🔄', text: 'Acompanha cada contato do primeiro olá ao fechamento' },
  { icon: '💬', text: 'Reativa clientes inativos com timing e contexto certo' },
  { icon: '📊', text: 'Identifica oportunidades escondidas nos dados da conversa' },
  { icon: '⏰', text: 'Faz follow-up sem você precisar lembrar de nada' },
  { icon: '🔐', text: 'Trilha completa — quem fez o quê e quando' },
]

onMounted(async () => {
  const { gsap } = await import('gsap')
  const { ScrollTrigger } = await import('gsap/ScrollTrigger')
  gsap.registerPlugin(ScrollTrigger)

  gsap.fromTo(sectionRef.value?.querySelectorAll('.crm-reveal'),
    { y: 40, opacity: 0 },
    {
      y: 0, opacity: 1, duration: .8, stagger: .12, ease: 'power3.out',
      scrollTrigger: { trigger: sectionRef.value, start: 'top 68%' }
    }
  )

  // Contador animado
  ScrollTrigger.create({
    trigger: counterEl.value,
    start: 'top 80%',
    once: true,
    onEnter: () => {
      const obj = { val: 0 }
      gsap.to(obj, {
        val: 847,
        duration: 2.2,
        ease: 'power2.out',
        onUpdate: () => {
          if (counterEl.value) counterEl.value.textContent = Math.round(obj.val).toLocaleString('pt-BR')
        }
      })
    }
  })
})
</script>

<template>
  <section id="crm" ref="sectionRef" class="py-16 px-6 relative overflow-hidden">

    <div class="absolute inset-0 bg-gradient-to-br from-emerald-950/30 via-[#07070f] to-[#07070f]" />
    <div class="absolute top-0 left-1/4 w-[600px] h-[600px] bg-emerald-500/6 rounded-full blur-3xl pointer-events-none" />

    <div class="relative max-w-7xl mx-auto">

      <!-- Badge -->
      <div class="text-center mb-10">
        <div class="inline-flex items-center gap-2.5 px-5 py-2 rounded-full border border-emerald-500/35 bg-emerald-500/12 text-emerald-300 text-sm font-bold crm-reveal uppercase tracking-widest">
          <span class="text-base">🚀</span> Novo — CRM Autônomo
        </div>
      </div>

      <div class="grid lg:grid-cols-2 gap-16 items-center">

        <!-- Texto -->
        <div>
          <h2
            class="display text-white leading-[.92] tracking-tight mb-6 crm-reveal"
            style="font-size: clamp(2.6rem, 5.5vw, 5rem);"
          >
            O vendedor<br />
            <span class="g-text-green">que nunca dorme.</span>
          </h2>

          <p class="text-slate-300 text-xl leading-relaxed mb-4 crm-reveal" style="font-weight:300;">
            Enquanto você descansa, o Genius acompanha cada lead, responde no
            momento certo, qualifica, aquece e conduz até o fechamento.
          </p>

          <p class="text-slate-500 text-base leading-relaxed mb-10 crm-reveal">
            Não é funil manual. Não é chatbot avulso. É uma inteligência que conhece
            o histórico de cada cliente e age com contexto real.
          </p>

          <div class="space-y-2.5 mb-10 crm-reveal">
            <div
              v-for="cap in capabilities"
              :key="cap.text"
              class="flex items-start gap-3 px-3 py-2.5 rounded-xl hover:bg-white/3 transition-colors"
            >
              <span class="text-lg shrink-0">{{ cap.icon }}</span>
              <p class="text-slate-300 text-sm leading-relaxed">{{ cap.text }}</p>
            </div>
          </div>

          <a
            href="#demo"
            class="crm-reveal inline-flex items-center gap-3 px-8 py-4 rounded-xl bg-emerald-500 hover:bg-emerald-400 text-black font-extrabold text-base transition-all hover:scale-[1.04] active:scale-95 glow-green display"
          >
            Quero o CRM Autônomo
            <svg class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
              <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3"/>
            </svg>
          </a>
        </div>

        <!-- Painel visual -->
        <div class="crm-reveal">
          <div class="p-px rounded-2xl" style="background: linear-gradient(135deg, rgba(0,232,123,.3), rgba(14,165,233,.2), rgba(167,139,250,.15));">
            <div class="rounded-2xl bg-[#09090f] p-6">

              <!-- Header -->
              <div class="flex items-center justify-between mb-6">
                <div>
                  <div class="display font-bold text-white">CRM Autônomo</div>
                  <div class="text-slate-600 text-xs mono mt-0.5">Pipeline gerenciado por IA</div>
                </div>
                <div class="flex items-center gap-1.5 text-emerald-400 text-xs font-bold mono">
                  <span class="w-1.5 h-1.5 rounded-full bg-emerald-400 pulse-dot" />
                  IA ativa
                </div>
              </div>

              <!-- Métrica -->
              <div class="p-5 rounded-xl mb-4" style="background: rgba(0,232,123,.07); border: 1px solid rgba(0,232,123,.15);">
                <div class="display font-black text-emerald-400" style="font-size:2.8rem;" ref="counterEl">0</div>
                <div class="text-slate-400 text-sm mt-1">leads qualificados esta semana</div>
                <div class="text-emerald-500 text-xs mt-1.5 mono font-medium">↑ 34% vs semana anterior</div>
              </div>

              <!-- Pipeline -->
              <div class="space-y-2">
                <div
                  v-for="lead in crmLeads"
                  :key="lead.name"
                  class="flex items-center justify-between p-3 rounded-xl transition-colors hover:bg-white/3"
                  style="border: 1px solid rgba(255,255,255,0.05);"
                >
                  <div class="flex items-center gap-3">
                    <div
                      class="w-8 h-8 rounded-full flex items-center justify-center text-xs font-bold text-white shrink-0"
                      :style="`background: ${lead.color}22; border: 1px solid ${lead.color}33;`"
                    >
                      {{ lead.initials }}
                    </div>
                    <div>
                      <div class="text-white text-xs font-semibold">{{ lead.name }}</div>
                      <div class="text-slate-600 text-xs mono">{{ lead.action }}</div>
                    </div>
                  </div>
                  <div class="text-xs font-bold mono" :style="`color: ${lead.color};`">{{ lead.status }}</div>
                </div>
              </div>

              <div class="mt-4 text-center text-xs text-slate-700 mono">
                Genius atualizou automaticamente há 2 minutos
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Frase de impacto final -->
      <div class="mt-20 text-center crm-reveal">
        <p class="display text-2xl font-black text-slate-300 max-w-3xl mx-auto leading-tight tracking-tight">
          "Do primeiro contato ao fechamento.
          <span class="g-text-green">Automático.</span>"
        </p>
      </div>
    </div>
  </section>
</template>
