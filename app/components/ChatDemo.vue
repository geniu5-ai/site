<script setup>
const activeIdx = ref(0)
const messages = ref([])
const isTyping = ref(false)
let playTimeout = null

const sectors = [
  {
    label: 'Clínica',
    icon: '🏥',
    color: '#00e87b',
    script: [
      { from: 'client', text: 'Boa tarde! Vocês fazem avaliação odontológica?' },
      { from: 'agent',  text: 'Boa tarde! Sim, fazemos. 😊 Você está buscando uma avaliação de rotina, limpeza ou está sentindo alguma dor?' },
      { from: 'client', text: 'Estou com uma dor no dente de trás e queria saber o preço.' },
      { from: 'agent',  text: 'Entendo. Para dor aguda, encaixamos como urgência. Posso verificar os próximos horários disponíveis ainda hoje?' },
      { from: 'client', text: 'Sim, por favor!' },
      { from: 'agent',  text: 'Temos às 15h e 17h30 hoje. Qual prefere? Já posso confirmar o seu horário e enviar o endereço.' },
    ],
  },
  {
    label: 'Imobiliária',
    icon: '🏠',
    color: '#0ea5e9',
    script: [
      { from: 'client', text: 'Vi o anúncio do apartamento de 2 quartos. Ainda está disponível?' },
      { from: 'agent',  text: 'Sim, está disponível! São 72m², 2 quartos sendo 1 suíte, vaga coberta. Você busca para morar ou investimento?' },
      { from: 'client', text: 'Para morar. Tem garagem?' },
      { from: 'agent',  text: 'Tem sim — 1 vaga coberta inclusa. O condomínio é R$ 480/mês e fica em Pinheiros, próximo ao metrô. Quer agendar uma visita?' },
      { from: 'client', text: 'Quero sim! Pode ser sábado?' },
      { from: 'agent',  text: 'Perfeito. Temos horários no sábado às 10h ou 14h. Qual fica melhor pra você? Vou passar o contato do corretor responsável.' },
    ],
  },
  {
    label: 'Advocacia',
    icon: '⚖️',
    color: '#a78bfa',
    script: [
      { from: 'client', text: 'Olá, fui demitido sem justa causa e acho que não recebi tudo certo.' },
      { from: 'agent',  text: 'Olá! Entendo a situação. Para avaliarmos os seus direitos, me diga: há quanto tempo você estava na empresa e recebeu FGTS + 40% de multa?' },
      { from: 'client', text: '3 anos. Recebi FGTS mas não sei se a multa veio certa.' },
      { from: 'agent',  text: 'Com 3 anos de carteira, você tem direito à multa de 40% + aviso prévio de 43 dias + saldo de salário. Vou te conectar com um advogado trabalhista para uma análise gratuita. Pode me passar seu nome?' },
      { from: 'client', text: 'Claro, me chamo Carlos.' },
      { from: 'agent',  text: 'Perfeito, Carlos! Vou agendar uma consulta gratuita de 20min ainda essa semana. Prefere manhã ou tarde?' },
    ],
  },
  {
    label: 'E-commerce',
    icon: '🛒',
    color: '#f59e0b',
    script: [
      { from: 'client', text: 'Fiz um pedido há 5 dias e ainda não chegou. O número é #94821.' },
      { from: 'agent',  text: 'Olá! Já consultei o pedido #94821. Ele saiu do nosso centro de distribuição ontem e está com entrega prevista para amanhã pelo período da tarde. 📦' },
      { from: 'client', text: 'Tá bom. E se eu quiser trocar o tamanho, como faço?' },
      { from: 'agent',  text: 'Você tem até 30 dias após o recebimento para solicitar troca sem custo. Quando chegar, basta me acionar aqui e eu abro o pedido de troca. Mais alguma coisa posso ajudar?' },
      { from: 'client', text: 'Não, muito obrigado!' },
      { from: 'agent',  text: 'Por nada! Qualquer dúvida é só chamar aqui. Boa tarde! 😊' },
    ],
  },
]

function selectSector(idx) {
  if (idx === activeIdx.value) return
  activeIdx.value = idx
  restartDemo()
}

function restartDemo() {
  clearTimeout(playTimeout)
  messages.value = []
  isTyping.value = false
  playScript()
}

function playScript() {
  const script = sectors[activeIdx.value].script
  let delay = 600

  script.forEach((msg, i) => {
    if (msg.from === 'agent') {
      playTimeout = setTimeout(() => {
        isTyping.value = true
        setTimeout(() => {
          isTyping.value = false
          messages.value.push({ ...msg, id: Date.now() + i })
        }, 900)
      }, delay)
      delay += 1800
    } else {
      playTimeout = setTimeout(() => {
        messages.value.push({ ...msg, id: Date.now() + i })
      }, delay)
      delay += 1300
    }
  })
}

onMounted(() => {
  playScript()
})

onUnmounted(() => {
  clearTimeout(playTimeout)
})

const chatEnd = ref(null)
watch(messages, async () => {
  await nextTick()
  chatEnd.value?.scrollIntoView({ behavior: 'smooth', block: 'nearest' })
})

const activeColor = computed(() => sectors[activeIdx.value].color)
</script>

<template>
  <section id="demo" class="py-16 px-6 relative overflow-hidden">

    <div class="absolute inset-0 bg-gradient-to-b from-transparent via-[#070712] to-transparent pointer-events-none" />
    <div
      class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[700px] h-[500px] rounded-full blur-[120px] opacity-10 pointer-events-none transition-all duration-700"
      :style="`background: ${activeColor};`"
    />

    <div class="relative max-w-6xl mx-auto">

      <!-- Header -->
      <div class="text-center mb-14">
        <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full border border-emerald-500/30 bg-emerald-500/8 text-emerald-400 text-xs font-semibold mb-6 uppercase tracking-widest">
          Demonstração ao vivo
        </div>
        <h2 class="display text-white leading-[.95] tracking-tight" style="font-size: clamp(2rem, 4.5vw, 3.4rem);">
          Veja o agente trabalhando<br />
          <span class="g-text">no seu setor.</span>
        </h2>
        <p class="text-slate-400 text-base mt-4 max-w-lg mx-auto">
          Escolha um segmento e veja como o Genius conduz uma conversa real — qualificando, respondendo e convertendo.
        </p>
      </div>

      <!-- Sector selector -->
      <div class="flex flex-wrap justify-center gap-3 mb-10">
        <button
          v-for="(sector, idx) in sectors"
          :key="idx"
          @click="selectSector(idx)"
          class="flex items-center gap-2 px-4 py-2 rounded-xl text-sm font-semibold border transition-all duration-200"
          :class="activeIdx === idx
            ? 'text-white border-transparent scale-[1.03]'
            : 'text-slate-400 border-white/10 hover:border-white/20 hover:text-white'"
          :style="activeIdx === idx ? `background: ${sector.color}20; border-color: ${sector.color}40; color: ${sector.color};` : ''"
        >
          <span>{{ sector.icon }}</span>
          {{ sector.label }}
        </button>
      </div>

      <!-- Chat window -->
      <div class="max-w-2xl mx-auto">
        <div class="rounded-2xl border border-white/10 bg-[#0a0a14]/80 backdrop-blur-md overflow-hidden shadow-2xl">

          <!-- Chat header -->
          <div class="flex items-center gap-3 px-5 py-4 border-b border-white/8">
            <div
              class="w-9 h-9 rounded-full flex items-center justify-center text-sm font-bold display transition-all"
              :style="`background: ${activeColor}20; color: ${activeColor};`"
            >
              G
            </div>
            <div>
              <div class="text-white text-sm font-semibold display">Genius · {{ sectors[activeIdx].label }}</div>
              <div class="flex items-center gap-1.5 text-emerald-400 text-xs">
                <span class="w-1.5 h-1.5 rounded-full bg-emerald-400 inline-block pulse-dot" />
                Agente ativo · responde em segundos
              </div>
            </div>
            <div class="ml-auto flex gap-1.5">
              <div class="w-3 h-3 rounded-full bg-white/10" />
              <div class="w-3 h-3 rounded-full bg-white/10" />
              <div class="w-3 h-3 rounded-full bg-white/10" />
            </div>
          </div>

          <!-- Messages -->
          <div class="h-96 overflow-y-auto px-5 py-5 flex flex-col gap-3 scroll-smooth" style="scroll-behavior: smooth;">
            <TransitionGroup name="msg-anim">
              <div
                v-for="msg in messages"
                :key="msg.id"
                class="flex"
                :class="msg.from === 'client' ? 'justify-end' : 'justify-start'"
              >
                <div
                  class="max-w-[80%] px-4 py-2.5 rounded-2xl text-sm leading-relaxed"
                  :class="msg.from === 'client'
                    ? 'bg-white/8 text-slate-200 rounded-br-sm'
                    : 'text-slate-100 rounded-bl-sm'"
                  :style="msg.from === 'agent' ? `background: ${activeColor}18; border: 1px solid ${activeColor}25;` : ''"
                >
                  {{ msg.text }}
                </div>
              </div>
            </TransitionGroup>

            <!-- Typing indicator -->
            <Transition name="msg-anim">
              <div v-if="isTyping" class="flex justify-start">
                <div
                  class="px-4 py-3 rounded-2xl rounded-bl-sm flex items-center gap-1"
                  :style="`background: ${activeColor}14; border: 1px solid ${activeColor}22;`"
                >
                  <span class="w-1.5 h-1.5 rounded-full animate-bounce" :style="`background: ${activeColor}; animation-delay: 0ms;`" />
                  <span class="w-1.5 h-1.5 rounded-full animate-bounce" :style="`background: ${activeColor}; animation-delay: 150ms;`" />
                  <span class="w-1.5 h-1.5 rounded-full animate-bounce" :style="`background: ${activeColor}; animation-delay: 300ms;`" />
                </div>
              </div>
            </Transition>
            <div ref="chatEnd" />
          </div>

          <!-- Input bar (decorative) -->
          <div class="px-5 py-4 border-t border-white/8 flex items-center gap-3">
            <div class="flex-1 px-4 py-2.5 rounded-xl bg-white/5 text-slate-600 text-sm">
              Digite sua mensagem...
            </div>
            <button
              class="w-9 h-9 rounded-xl flex items-center justify-center transition-all hover:scale-105"
              :style="`background: ${activeColor}; color: #07070f;`"
            >
              <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24">
                <path d="M2.01 21L23 12 2.01 3 2 10l15 2-15 2z"/>
              </svg>
            </button>
          </div>
        </div>

        <!-- Replay -->
        <div class="flex justify-center mt-6">
          <button
            @click="restartDemo"
            class="text-slate-500 text-xs hover:text-white transition-colors flex items-center gap-1.5"
          >
            <svg class="w-3.5 h-3.5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15"/>
            </svg>
            Rever demonstração
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.msg-anim-enter-active { animation: slide-msg .3s ease forwards; }
.msg-anim-leave-active { animation: slide-msg .2s ease reverse forwards; }
@keyframes slide-msg {
  from { opacity: 0; transform: translateY(10px) scale(.97); }
  to   { opacity: 1; transform: translateY(0)   scale(1);   }
}
</style>
