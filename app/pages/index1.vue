<script setup lang="ts">
const menuAberto = ref(false)

const { data: posts } = await useAsyncData('home-posts', () =>
  queryCollection('blog').order('date', 'DESC').limit(3).all()
)

const areas = [
  { titulo: 'Direito Imobiliário', texto: 'Locação, contratos de compra e venda, análise de risco, retificação de área e usucapião.' },
  { titulo: 'Direito de Família', texto: 'Divórcio, guarda, união estável e alimentos, com atendimento humanizado.' },
  { titulo: 'Sucessões', texto: 'Inventários, partilhas e planejamento sucessório, presencial e online.' },
  { titulo: 'Direito do Consumidor', texto: 'Defesa dos seus direitos nas relações de consumo.' },
  { titulo: 'Ações Indenizatórias', texto: 'Danos morais e materiais, com busca pela reparação justa.' },
  { titulo: 'Execuções', texto: 'Processos de execução, cobranças e garantias.' }
]

const dataFormatada = (data: string) =>
  new Date(data).toLocaleDateString('pt-BR', { day: '2-digit', month: '2-digit', year: 'numeric' })

function enviarFormulario(e: Event) {
  const form = e.target as HTMLFormElement
  const dados = new FormData(form)
  const assunto = encodeURIComponent(`Contato pelo site — ${dados.get('nome')}`)
  const corpo = encodeURIComponent(`${dados.get('mensagem')}\n\n${dados.get('nome')} — ${dados.get('email')}`)
  window.location.href = `mailto:ellensgarbiero.adv@gmail.com?subject=${assunto}&body=${corpo}`
}
</script>

<template>
  <div>
    <nav class="nav">
      <a href="#inicio"><img src="/img/logo.png" alt="Ellen Sgarbiero — Advocacia" /></a>
      <button class="menu-btn" @click="menuAberto = !menuAberto">☰</button>
      <ul class="nav-links" :class="{ aberto: menuAberto }" @click="menuAberto = false">
        <li><a href="#inicio">Início</a></li>
        <li><a href="#apresentacao">Apresentação</a></li>
        <li><a href="#areas">Áreas de Atuação</a></li>
        <li><a href="#agenda">Agenda</a></li>
        <li><a href="#blog">Últimos Casos</a></li>
        <li><a href="#contato">Contato</a></li>
      </ul>
    </nav>

    <!-- HERO -->
    <section id="inicio" class="hero">
      <img src="/img/foto-ellen.png" alt="Dra. Ellen Sgarbiero" />
      <div class="hero-texto">
        <h1>Ellen Sgarbiero</h1>
        <p class="subtitulo">Advocacia especializada em Direito Imobiliário</p>
        <p>Atendimento presencial e online em todo o território nacional.</p>
        <div class="hero-botoes">
          <a href="#agenda" class="btn btn-secundario">Agendar consulta</a>
          <a href="#contato" class="btn btn-primario">Fale comigo</a>
        </div>
      </div>
    </section>

    <!-- APRESENTAÇÃO -->
    <section id="apresentacao">
      <div class="container">
        <h2>Apresentação</h2>
        <p>Meu nome é Ellen Sgarbiero, graduada em Direito pelo Instituto de Ciências Aplicada - ISCA, na cidade de Limeira - Estado de São Paulo, advogada desde 2013, atendo clientes na forma presencial e online em todo o território nacional.</p>
        <p>No decorrer desses anos, adquiri uma vasta experiência na resolução de conflitos em demandas judiciais e extrajudiciais, especialmente nas áreas de família, sucessões, consumidor, indenizatórias, execuções e ramo imobiliário.</p>
        <p>Minha missão é oferecer um serviço jurídico personalizado e criar valores e soluções inteligentes com qualidade de excelência, buscando cada vez mais a implantação da advocacia preventiva, trazendo segurança jurídica aos meus clientes.</p>
      </div>
    </section>

    <!-- ÁREAS -->
    <section id="areas" class="secao-clara">
      <div class="container">
        <h2>Áreas de Atuação</h2>
        <div class="areas-grid">
          <div v-for="area in areas" :key="area.titulo" class="area-card">
            <h3>{{ area.titulo }}</h3>
            <p>{{ area.texto }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- AGENDA -->
    <section id="agenda">
      <div class="container">
        <h2>Agende sua consulta</h2>
        <div class="agenda-box">
          <header>Calendário de atendimentos</header>
          <!-- EMBED: substituir este bloco pelo iframe do Google Calendar ou Outlook Calendar -->
          <div class="agenda-embed">
            <iframe
              src="URL_DO_CALENDARIO_AQUI"
              scrolling="no"
              loading="lazy"
              title="Agenda da Dra. Ellen"
            ></iframe>
          </div>
          <p class="agenda-nota">A agenda da Dra. Ellen aparece aqui em tempo real — sincronizada com o e-mail dela.</p>
        </div>
      </div>
    </section>

    <!-- BLOG -->
    <section id="blog" class="secao-clara">
      <div class="container">
        <h2>Últimos casos</h2>
        <!-- CMS: posts alimentados via painel Decap CMS pela Dra. Ellen -->
        <div class="posts-grid">
          <NuxtLink v-for="post in posts" :key="post.path" :to="post.path" class="post-card">
            <div class="meta">
              <span>{{ dataFormatada(post.date) }}</span>
              <span class="categoria">{{ post.category }}</span>
            </div>
            <h3>{{ post.title }}</h3>
          </NuxtLink>
        </div>
        <div style="text-align: center; margin-top: 2rem">
          <NuxtLink to="/blog" class="btn btn-primario">Ver todos os posts</NuxtLink>
        </div>
      </div>
    </section>

    <!-- CONTATO -->
    <section id="contato">
      <div class="container contato-grid">
        <div class="contato-info">
          <h2>Entre em contato</h2>
          <a href="mailto:ellensgarbiero.adv@gmail.com">ellensgarbiero.adv@gmail.com</a>
          <a href="tel:+5519981029844">Cel: (19) 98102-9844</a>
          <div class="redes">
            <a href="https://wa.me/5519981029844" target="_blank" rel="noopener" title="WhatsApp">W</a>
            <a href="https://www.instagram.com/ellensgarbiero.adv/" target="_blank" rel="noopener" title="Instagram">IG</a>
            <a href="https://www.facebook.com/ellensgarbieroadv/" target="_blank" rel="noopener" title="Facebook">FB</a>
            <a href="https://www.linkedin.com/in/ellensgarbiero/" target="_blank" rel="noopener" title="LinkedIn">IN</a>
          </div>
        </div>
        <form @submit.prevent="enviarFormulario">
          <div class="form-grupo">
            <label for="nome">Nome</label>
            <input id="nome" name="nome" type="text" required />
          </div>
          <div class="form-grupo">
            <label for="email">E-mail</label>
            <input id="email" name="email" type="email" required />
          </div>
          <div class="form-grupo">
            <label for="mensagem">Mensagem</label>
            <textarea id="mensagem" name="mensagem" rows="5" required></textarea>
          </div>
          <button type="submit" class="btn btn-primario">Enviar</button>
        </form>
      </div>
    </section>

    <footer>
      <NuxtLink to="/" class="marca">
      <img src="/img/logo.png" alt="Logo Ellen Sgarbiero">
      <span class="marca-texto">
        <span class="marca-nome">Ellen Sgarbiero</span>
        <span class="marca-sub">Advocacia</span>
      </span>
    </NuxtLink>
      <p class="oab">OAB/SP 000.000</p>
    </footer>
  </div>
</template>