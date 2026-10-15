<script setup>
const { data: posts } = await useAsyncData('posts-todos', () =>
  queryCollection('blog').order('date', 'DESC').all()
)

const formatarData = (data) =>
  new Date(data).toLocaleDateString('pt-BR', { timeZone: 'UTC' })

useHead({ title: 'Últimos casos — Ellen Sgarbiero' })
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
    </nav>

    <section>
      <div class="container">
        <div class="cabecalho-secao">
          <span class="kicker">Blog jurídico</span>
          <h2>Últimos casos</h2>
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
          <NuxtLink to="/" class="voltar">← Voltar ao início</NuxtLink>
        </div>
      </div>
    </section>

    <footer>
      <img src="/img/logo.png" alt="Logo Ellen Sgarbiero">
      <p class="oab">OAB/SP 000.000</p>
      <p>© {{ new Date().getFullYear() }} Ellen Sgarbiero — Advocacia. Todos os direitos reservados.</p>
    </footer>
  </div>
</template>