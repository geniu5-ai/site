<script setup>
const title = 'Política de Privacidade — Genius'
useSeoMeta({
  title,
  description: 'Como o Genius coleta, usa, protege e compartilha dados pessoais, incluindo o acesso ao Google Drive.',
  robots: 'index, follow'
})
</script>

<template>
  <LegalPage title="Política de Privacidade" updated="5 de novembro de 2026">
    <p>
      Esta política explica como o <strong>Genius</strong> (plataforma de atendimento, CRM e agentes de IA operada pela Genius Labs,
      "nós") trata dados pessoais, em conformidade com a Lei Geral de Proteção de Dados (LGPD, Lei 13.709/2018).
    </p>

    <h2>1. Quem é o controlador e quem é o operador</h2>
    <p>
      Em relação aos dados dos <strong>nossos clientes</strong> (empresas que contratam o Genius e seus usuários), somos controladores.
      Em relação aos dados dos <strong>contatos finais</strong> dessas empresas (pessoas que conversam com seus agentes), a empresa
      contratante é a controladora e nós atuamos como operadores, tratando os dados apenas conforme as instruções dela.
    </p>

    <h2>2. Dados que coletamos</h2>
    <ul>
      <li><strong>Conta e empresa:</strong> nome, e-mail, senha (armazenada com hash), nome da empresa, CNPJ, telefone e endereço.</li>
      <li><strong>Conversas e atendimento:</strong> mensagens, nome e identificadores de contatos nos canais conectados (WhatsApp, Instagram e outros), histórico e dados de CRM.</li>
      <li><strong>Arquivos enviados:</strong> tabelas de preços, políticas, documentos e imagens que o cliente envia para o agente conhecer o negócio.</li>
      <li><strong>Pagamento:</strong> tratado pelo Stripe; não armazenamos números de cartão.</li>
      <li><strong>Uso e diagnóstico:</strong> registros técnicos de erros e desempenho, sem conteúdo de conversas.</li>
    </ul>

    <h2>3. Acesso ao Google Drive e dados de usuário do Google</h2>
    <p>
      Se o cliente optar por conectar o Google Drive, solicitamos o escopo <strong>somente leitura</strong>
      (<code>drive.readonly</code>) e o e-mail da conta Google. Usamos esse acesso exclusivamente para listar e importar, a pedido do cliente,
      os arquivos que ele escolher, para que o agente de IA responda com base neles.
    </p>
    <ul>
      <li>Não alteramos, apagamos nem criamos arquivos no seu Drive.</li>
      <li>Não vendemos esses dados, não os usamos para publicidade e não os transferimos a terceiros, exceto a prestadores necessários para operar o serviço (item 5).</li>
      <li>O uso e a transferência das informações recebidas das APIs do Google seguem a
        <a href="https://developers.google.com/terms/api-services-user-data-policy" target="_blank" rel="noopener">Política de Dados do Usuário dos Serviços de API do Google</a>,
        incluindo os requisitos de Uso Limitado.</li>
      <li>O token de acesso é armazenado cifrado. Você pode desconectar a qualquer momento em <em>Conexões</em> dentro do app; ao desconectar, revogamos o acesso no Google.
        Também é possível revogar em <a href="https://myaccount.google.com/permissions" target="_blank" rel="noopener">myaccount.google.com/permissions</a>.</li>
    </ul>

    <h2>4. Para que usamos os dados</h2>
    <ul>
      <li>Prestar o serviço contratado (atendimento, CRM, agentes de IA, integrações);</li>
      <li>Autenticar usuários, prevenir fraude e garantir a segurança;</li>
      <li>Processar pagamentos e emitir cobranças;</li>
      <li>Suporte, comunicação sobre o serviço e cumprimento de obrigações legais.</li>
    </ul>
    <p>As bases legais incluem a execução de contrato, o legítimo interesse, o cumprimento de obrigação legal e, quando necessário, o consentimento.</p>

    <h2>5. Com quem compartilhamos</h2>
    <p>
      Compartilhamos dados apenas com prestadores necessários à operação, sob obrigações de confidencialidade e segurança: infraestrutura e
      banco de dados (Supabase, Vercel, Cloudflare), armazenamento de arquivos (Cloudflare R2), pagamentos (Stripe), provedores de canais de
      mensagens (como Meta/WhatsApp) e provedores de modelos de IA usados para gerar respostas. Podemos divulgar dados quando exigido por lei.
      Alguns prestadores ficam fora do Brasil; nesses casos adotamos as salvaguardas previstas na LGPD.
    </p>

    <h2>6. Segurança</h2>
    <p>
      Usamos conexão criptografada (HTTPS), controle de acesso por empresa, isolamento de dados entre clientes, tokens cifrados e arquivos em
      armazenamento privado. Nenhum sistema é 100% imune; em caso de incidente relevante, notificaremos os afetados e a ANPD conforme a lei.
    </p>

    <h2>7. Retenção</h2>
    <p>
      Mantemos os dados enquanto a conta estiver ativa e pelo prazo necessário para cumprir obrigações legais. Ao encerrar a conta, os dados
      são excluídos ou anonimizados em prazo razoável, salvo guarda obrigatória por lei.
    </p>

    <h2 id="lgpd">8. Seus direitos (LGPD)</h2>
    <p>
      Você pode solicitar confirmação de tratamento, acesso, correção, anonimização, portabilidade, eliminação, informação sobre
      compartilhamento e revogação de consentimento. Para dados de contatos de uma empresa cliente, direcionaremos o pedido à empresa
      controladora. Escreva para o e-mail abaixo.
    </p>

    <h2>9. Cookies</h2>
    <p>Usamos apenas cookies essenciais (sessão e preferências de uso do app). Não usamos cookies de publicidade.</p>

    <h2>10. Crianças</h2>
    <p>O Genius é destinado a empresas e não se dirige a menores de 18 anos.</p>

    <h2>11. Alterações</h2>
    <p>Podemos atualizar esta política; a data no topo indica a versão vigente e mudanças relevantes serão comunicadas.</p>

    <h2>12. Contato</h2>
    <p>Dúvidas e solicitações de titulares: <a href="mailto:contato@geniuslabs.pro">contato@geniuslabs.pro</a>.</p>
  </LegalPage>
</template>
