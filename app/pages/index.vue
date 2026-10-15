<script setup>
const { data: posts } = await useAsyncData('posts-home', () =>
  queryCollection('blog').order('date', 'DESC').limit(3).all()
)

const menuAberto = ref(false)

const formatarData = (data) =>
  new Date(data).toLocaleDateString('pt-BR', { timeZone: 'UTC' })

const areas = [
  {
    titulo: 'Direito Imobiliário',
    principal: true,
    icone: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 10.5 12 3l9 7.5"/><path d="M5 9.5V21h14V9.5"/><path d="M10 21v-6h4v6"/></svg>',
    texto: 'Locação, elaboração e revisão de contratos de compra e venda, análise aprofundada de risco, retificação de área e ações de usucapião. '
  },
  {
    titulo: 'Direito Internacional de Família',
    principal: true,
    icone: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><path d="M14 2v6h6"/><path d="m9 15 2 2 4-4"/></svg>',
    texto: 'Divórcio consensual e litigioso, guarda e convivência dos filhos, pensão alimentícia, reconhecimento de união estável e acordos extrajudiciais. '
  },
  {
    titulo: 'Sucessões',
    icone: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 20h9"/><path d="M16.5 3.5a2.1 2.1 0 0 1 3 3L7 19l-4 1 1-4z"/></svg>',
    texto: 'Inventários judiciais e em cartório (extrajudiciais), partilha amigável de patrimônio, testamentos e planejamento sucessório patrimonial seguro. '
  },
  {
    titulo: 'Direito do Consumidor',
    icone: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 12a9 9 0 1 0 3-6.7L3 8"/><path d="M3 3v5h5"/></svg>',
    texto: 'Proteção contra cláusulas abusivas, cobranças indevidas, vícios de produtos e serviços, atrasos e descumprimentos de acordos de consumo. '
  },
  {
    titulo: 'Ações Indenizatórias',
    icone: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 3v18"/><path d="M5 7h14"/><path d="m5 7-3 6a3.5 3.5 0 0 0 6 0z"/><path d="m19 7-3 6a3.5 3.5 0 0 0 6 0z"/><path d="M8 21h8"/></svg>',
    texto: 'Responsabilidade civil contratual e extracontratual, reparação por danos materiais, perdas e danos e indenizações por danos morais. '
  },
  {
    titulo: 'Execuções',
    icone: '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 22s8-3 8-10V5l-8-3-8 3v7c0 7 8 10 8 10z"/></svg>',
    texto: 'Cobrança de títulos executivos judiciais e extrajudiciais, localização e recuperação de bens, penhoras e embargos à execução. '
  }
]

useHead({ title: 'Ellen Sgarbiero — Advocacia Imobiliária' })
</script>

<template>
  <div>
    <nav class="nav">
      <NuxtLink to="/" class="marca">
      <img src="/img/logo.png" alt="Logo Ellen Sgarbiero">
        <span class="marca-texto">
          <span class="marca-nome">Ellen Sgarbiero</span>
          <span class="marca-sub">Advocacia</span>
        </span>
      </NuxtLink>
      <button class="menu-btn" @click="menuAberto = !menuAberto">☰</button>
      <ul class="nav-links" :class="{ aberto: menuAberto }">
        <li><a href="#inicio" @click="menuAberto = false">Início</a></li>
        <li><a href="#apresentacao" @click="menuAberto = false">Apresentação</a></li>
        <li><a href="#areas" @click="menuAberto = false">Áreas de Atuação</a></li>
        <li><a href="#agenda" @click="menuAberto = false">Agenda</a></li>
        <li><a href="#casos" @click="menuAberto = false">Últimos Casos</a></li>
        <li><a href="#contato" @click="menuAberto = false">Contato</a></li>
      </ul>
    </nav>

    <section class="hero" id="inicio">
      <img src="/img/foto-ellen.png" alt="Ellen Sgarbiero, advogada">
      <div class="hero-texto">
        <h1>Ellen Sgarbiero</h1>
        <p class="subtitulo">Advocacia especializada em Direito Imobiliário e Direito Internacional de Família</p>
        <p>Assessoria jurídica completa em questões envolvendo imóveis e famílias com conexão internacional — da regularização da documentação à defesa dos seus direitos em juízo.</p>
        <div class="hero-botoes">
          <a href="#agenda" class="btn btn-primario">Agendar consulta</a>
          <a href="#contato" class="btn btn-secundario">Fale comigo</a>
        </div>
      </div>
    </section>

    <section id="apresentacao" class="secao-apresentacao">
  <div class="container">
    <div class="cabecalho-secao">
      <span class="kicker">Conheça a advogada</span>
      <h2>Apresentação</h2>
      <p class="cabecalho-apoio">Advocacia imobiliária com atendimento próximo e linguagem clara — você entende cada etapa do seu caso.</p>
    </div>

    <div class="apresentacao-card">
      <aside class="destaque">
        <img src="/img/foto-ellen2.png" alt="Ellen Sgarbiero, advogada" class="destaque-foto">
        <svg class="aspas" viewBox="0 0 24 24" width="30" height="30" fill="currentColor"><path d="M9.5 8C7 8 5 10 5 12.5 5 15 7 17 9.5 17c.3 0 .6 0 .9-.1-.5 1.6-1.8 2.9-3.4 3.6l1 1.5c3-1.3 5-4.2 5-7.5V12C13 9.8 11.5 8 9.5 8zm9 0C16 8 14 10 14 12.5c0 2.5 2 4.5 4.5 4.5.3 0 .6 0 .9-.1-.5 1.6-1.8 2.9-3.4 3.6l1 1.5c3-1.3 5-4.2 5-7.5V12c0-2.2-1.5-4-3.5-4z"/></svg>
        <p class="destaque-frase">Soluções inteligentes com qualidade de excelência e foco constante na advocacia preventiva.</p>
        <div class="destaque-stats">
          <div class="stat">
            <strong>10 anos</strong>
            <span>de atuação</span>
          </div>
          <div class="stat">
            <strong>+10 anos</strong>
            <span>Nacional</span>
          </div>
        </div>
      </aside>

      <div class="apresentacao-texto">
        <p><strong>Ellen Sgarbiero</strong> é advogada inscrita na OAB/SP, com atuação dedicada ao Direito Imobiliário. Seu trabalho é voltado aos problemas mais comuns — e mais delicados — que envolvem imóveis: documentação irregular, contratos mal redigidos, posse e propriedade.</p>
        <p>Atende clientes em Piracicaba e região, com atendimento próximo e linguagem clara: você entende cada etapa do seu caso, do primeiro contato à conclusão.</p>
        <p>Se você tem um imóvel com pendência, um contrato para revisar ou uma disputa em andamento, agende uma consulta e receba um diagnóstico claro do seu caso.</p>
      </div>
    </div>
  </div>
</section>

<section id="areas" class="secao-clara">
  <div class="container">
    <div class="cabecalho-secao">
      <span class="kicker">Especialidades jurídicas</span>
      <h2>Áreas de Atuação</h2>
      <p class="cabecalho-apoio">Assessoria completa em todas as demandas que envolvem o seu caso.</p>
    </div>
    <div class="areas-grid">
      <div v-for="area in areas" :key="area.titulo" class="area-card" :class="{ 'area-destaque': area.principal }">
        <span v-if="area.principal" class="area-badge">Especialidade principal</span>
        <div class="area-icone" v-html="area.icone"></div>
        <h3>{{ area.titulo }}</h3>
        <p>{{ area.texto }}</p>
      </div>
    </div>
  </div>
</section>

    <section id="agenda">
      <div class="container">
        <div class="cabecalho-secao">
          <span class="kicker">Disponibilidade em Tempo Real</span>
          <h2>Agende sua consulta</h2>
          <p class="cabecalho-apoio">Selecione uma data disponível para sua reunião presencial ou por videoconferência.</p>
        </div>
        <div class="agenda-box">
          <header>Calendário de atendimentos</header>
          <div class="agenda-embed">
            <iframe src="https://calendar.google.com/calendar/embed?src=576d06cff842ee1bc584a9f9976ae69ab597dbe079bd76e6139459bfe603d782%40group.calendar.google.com&ctz=America%2FSao_Paulo" loading="lazy" title="Calendário de atendimentos"></iframe>
          </div>
          <p class="agenda-nota">Escolha o melhor dia e horário diretamente no calendário acima.</p>
        </div>
      </div>
    </section>

    <section id="casos" class="secao-clara">
      <div class="container">
        <div class="cabecalho-secao">
          <span class="kicker">Artigos & Atualizações</span>
          <h2>Últimos casos</h2>
          <p class="cabecalho-apoio">Conteúdo informativo para orientar você sobre direitos patrimoniais e imobiliários.</p>
        </div>
        <div class="posts-grid">
      <NuxtLink v-for="post in posts" :key="post.path" :to="post.path" class="post-card">
        <div class="post-topo">
          <span class="categoria">{{ post.category }}</span>
          <span class="data">{{ formatarData(post.date) }}</span>
        </div>
        <h3>{{ post.title }}</h3>
        <p class="resumo">{{ post.description || 'Clique para ler o artigo completo.' }}</p>
        <span class="ler-artigo">Ler artigo <span aria-hidden="true">→</span></span>
      </NuxtLink>
    </div>

    <div class="posts-cta">
      <NuxtLink to="/blog" class="btn btn-primario">Ver todos os posts</NuxtLink>
    </div>
  </div>
</section>

    <section id="contato">
  <div class="container">
        <div class="cabecalho-secao">
          <span class="kicker">Canais Diretos</span>
          <h2>Entre em contato</h2>
          <p class="cabecalho-apoio">Envie sua dúvida ou agende um diagnóstico inicial com total discrição profissional.</p>
        </div>
    <div class="contato-card">
      <div class="contato-info">
        <h3>Dra. Ellen Sgarbiero</h3>
        <p>Entre em contato para agendar uma consulta ou tirar dúvidas sobre o seu caso. Retorno o mais breve possível.</p>

        <a class="contato-item" href="mailto:ellensgarbiero.adv@gmail.com">
          <span class="icone">
            <svg viewBox="0 0 24 24" width="18" height="18" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="m2 6 10 7 10-7"/></svg>
          </span>
          ellen@advocacia.com.br
        </a>

        <a class="contato-item" href="https://wa.me/5519981029844">
          <span class="icone">
            <svg viewBox="0 0 24 24" width="18" height="18" fill="none" stroke="currentColor" stroke-width="2"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72c.127.96.361 1.903.7 2.81a2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0 1 22 16.92z"/></svg>
          </span>
          (19) 98102-9844
        </a>

        <p class="localizacao">Piracicaba/SP — atendimento presencial e on-line</p>

        <div class="redes">
          <a href="#" aria-label="Instagram"><svg viewBox="0 0 24 24" width="18" height="18" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="2" width="20" height="20" rx="5"/><circle cx="12" cy="12" r="4"/><circle cx="17.5" cy="6.5" r="0.5" fill="currentColor"/></svg></a>
          <a href="#" aria-label="LinkedIn"><svg viewBox="0 0 24 24" width="18" height="18" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 1 1 0-4.125 2.062 2.062 0 0 1 0 4.125zM7.119 20.452H3.554V9h3.565v11.452z"/></svg></a>
          <a href="https://wa.me/5519999999999" aria-label="WhatsApp"><svg viewBox="0 0 24 24" width="18" height="18" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 0 1-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 0 1-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 0 1 2.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0 0 12.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 0 0 5.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 0 0-3.48-8.413z"/></svg></a>
          <a href="mailto:ellen@advocacia.com.br" aria-label="E-mail"><svg viewBox="0 0 24 24" width="18" height="18" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="m2 6 10 7 10-7"/></svg></a>
        </div>
      </div>

      <form action="mailto:ellen@advocacia.com.br" method="post" enctype="text/plain">
        <div class="form-grupo">
          <label for="nome">Nome Completo</label>
          <input id="nome" name="nome" type="text" required>
        </div>
        <div class="form-grupo">
          <label for="email">E-mail</label>
          <input id="email" name="email" type="email" required>
        </div>
        <div class="form-grupo">
          <label for="area">Área de Interesse</label>
          <select id="area" name="area">
            <option>Usucapião</option>
            <option>Regularização de Imóveis</option>
            <option>Contratos Imobiliários</option>
            <option>Distrato e Rescisão</option>
            <option>Inventário e Partilha</option>
            <option>Ações Possessórias</option>
            <option>Outro assunto</option>
          </select>
        </div>
        <div class="form-grupo">
          <label for="mensagem">Mensagem</label>
          <textarea id="mensagem" name="mensagem" rows="4" required></textarea>
        </div>
        <button type="submit" class="btn btn-enviar">
          Enviar mensagem
          <svg viewBox="0 0 24 24" width="16" height="16" fill="none" stroke="currentColor" stroke-width="2"><path d="m22 2-7 20-4-9-9-4z"/><path d="M22 2 11 13"/></svg>
        </button>
      </form>
    </div>
  </div>
</section>

    <footer>
        <img src="/img/logo.png" alt="Logo Ellen Sgarbiero">
        <span class="marca-texto">
          <span class="marca-nome">Ellen Sgarbiero</span>
          <span class="marca-sub">Advocacia</span>
        </span>
      <p class=""> </p>  
      <p class="oab">OAB/SP 000.000</p>
      <p>© {{ new Date().getFullYear() }} Ellen Sgarbiero — Advocacia. Todos os direitos reservados.</p>
    </footer>
  </div>
</template>