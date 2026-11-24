<script setup>
useSeoMeta({
  title: 'Genius — Seu negócio vende. O Genius cuida do resto.',
  description: 'CRM autônomo, inbox omnichannel e IA que transforma conversas em vendas — sem você gerenciar nada.',
  ogTitle: 'Genius — Atendimento que vende por você',
  ogDescription: 'Não é chatbot. É uma operação completa de atendimento com inteligência real.',
  twitterCard: 'summary_large_image'
})
useHead({
  htmlAttrs: { lang: 'pt-BR', class: 'dark' }
})
</script>

<template>
  <div style="background:#07070f; min-height:100vh; overflow-x:hidden;">
    <NuxtPage />
  </div>
</template>
