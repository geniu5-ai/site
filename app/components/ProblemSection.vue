<script setup>
const sectionRef = ref(null)

onMounted(async () => {
  const { gsap } = await import('gsap')
  const { ScrollTrigger } = await import('gsap/ScrollTrigger')
  gsap.registerPlugin(ScrollTrigger)

  gsap.fromTo(
    sectionRef.value?.querySelectorAll('.pain-row'),
    { x: -28, opacity: 0 },
    {
      x: 0, opacity: 1, duration: .65, stagger: .1, ease: 'power2.out',
      scrollTrigger: { trigger: sectionRef.value, start: 'top 72%' }
    }
  )
})

const pains = [
  { icon: '📱', text: 'Cada funcionário atende pelo celular pessoal. Nenhum histórico fica.' },
  { icon: '🔀', text: 'Mensagens espalhadas em WhatsApp, Instagram e DM sem nenhum controle.' },
  { icon: '🔁', text: 'O cliente repete tudo de novo a cada transferência.' },
  { icon: '👤', text: 'Quando alguém sai, leva o contato — e a relação — junto.' },
  { icon: '❓', text: 'Quem está cuidando desse lead? Ninguém consegue responder.' },
  { icon: '🤖', text: 'Chatbot instalado sem operação. Funciona às vezes. Irrita na maioria.' },
]
</script>

<template>
  <section ref="sectionRef" class="py-16 px-6 relative overflow-hidden">

    <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[700px] h-[400px] bg-red-500/4 rounded-full blur-3xl pointer-events-none" />

    <div class="max-w-6xl mx-auto grid md:grid-cols-2 gap-14 items-center">

      <!-- Left text -->
      <div>
        <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full border border-red-500/25 bg-red-500/8 text-red-400 text-xs font-semibold mb-6 uppercase tracking-widest">
          O problema real
        </div>
        <h2
          class="display leading-[1] tracking-tight mb-6 text-white"
          style="font-size: clamp(2.1rem, 4.5vw, 3.4rem);"
        >
          Seu atendimento está<br />
          <span style="color: #f87171;">funcionando no improviso.</span>
        </h2>
        <p class="text-slate-400 text-lg leading-relaxed max-w-sm">
          O negócio cresceu. O atendimento não acompanhou. Mensagens se perdem,
          a equipe perde o fio da meada e você não sabe quantas oportunidades foram embora hoje.
        </p>
      </div>

      <!-- Right pains -->
      <div class="space-y-3">
        <div
          v-for="(pain, i) in pains"
          :key="i"
          class="pain-row flex items-start gap-4 p-4 rounded-2xl g-card cursor-default"
        >
          <span class="text-xl shrink-0 mt-px">{{ pain.icon }}</span>
          <p class="text-slate-300 text-sm leading-relaxed">{{ pain.text }}</p>
        </div>
      </div>
    </div>
  </section>
</template>
