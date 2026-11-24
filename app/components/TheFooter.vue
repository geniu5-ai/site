<template>
  <footer class="border-t border-white/[.06] py-16 px-6">
    <div class="max-w-7xl mx-auto">
      <div class="grid md:grid-cols-4 gap-10 mb-12">

        <!-- Brand -->
        <div class="md:col-span-1">
          <div class="flex items-center gap-2.5 mb-5">
            <div class="w-7 h-7 rounded-lg bg-emerald-500 flex items-center justify-center glow-green">
              <span class="text-black font-black text-xs display">G</span>
            </div>
            <span class="display font-bold text-white">Genius</span>
          </div>
          <p class="text-slate-600 text-sm leading-relaxed mb-5">
            Atendimento inteligente para empresas brasileiras.
            Omni + IA + CRM Autônomo.
          </p>
          <div class="flex items-center gap-3">
            <a href="#" class="w-8 h-8 rounded-lg bg-white/4 hover:bg-white/8 border border-white/7 flex items-center justify-center text-slate-400 hover:text-white transition-all text-sm">W</a>
            <a href="#" class="w-8 h-8 rounded-lg bg-white/4 hover:bg-white/8 border border-white/7 flex items-center justify-center text-slate-400 hover:text-white transition-all text-sm">IG</a>
          </div>
        </div>

        <!-- Produto -->
        <div>
          <h4 class="display font-semibold text-white text-sm mb-5 uppercase tracking-widest">Produto</h4>
          <ul class="space-y-3">
            <li v-for="l in ['Como funciona', 'Inbox Omni', 'CRM Autônomo', 'IA Copiloto', 'Preços']" :key="l">
              <a href="#" class="text-slate-500 text-sm hover:text-white transition-colors">{{ l }}</a>
            </li>
          </ul>
        </div>

        <!-- Empresa -->
        <div>
          <h4 class="display font-semibold text-white text-sm mb-5 uppercase tracking-widest">Empresa</h4>
          <ul class="space-y-3">
            <li v-for="l in ['Sobre', 'Blog', 'Parceiros', 'Carreiras']" :key="l">
              <a href="#" class="text-slate-500 text-sm hover:text-white transition-colors">{{ l }}</a>
            </li>
          </ul>
        </div>

        <!-- Contato -->
        <div>
          <h4 class="display font-semibold text-white text-sm mb-5 uppercase tracking-widest">Contato</h4>
          <ul class="space-y-3">
            <li><a href="#" class="text-slate-500 text-sm hover:text-white transition-colors">WhatsApp</a></li>
            <li><a href="mailto:contato@geniuslabs.pro" class="text-slate-500 text-sm hover:text-white transition-colors">E-mail</a></li>
            <li><a href="#" class="text-slate-500 text-sm hover:text-white transition-colors">Central de ajuda</a></li>
          </ul>
        </div>
      </div>

      <div class="border-t border-white/[.06] pt-8 flex flex-col md:flex-row items-center justify-between gap-4">
        <p class="text-slate-700 text-xs mono">
          © {{ new Date().getFullYear() }} Genius. Todos os direitos reservados.
        </p>
        <div class="flex items-center gap-6">
          <NuxtLink to="/privacidade" class="text-slate-700 text-xs hover:text-white transition-colors">Privacidade</NuxtLink>
          <NuxtLink to="/termos" class="text-slate-700 text-xs hover:text-white transition-colors">Termos</NuxtLink>
          <NuxtLink to="/privacidade#lgpd" class="text-slate-700 text-xs hover:text-white transition-colors">LGPD</NuxtLink>
        </div>
      </div>
    </div>
  </footer>
</template>
