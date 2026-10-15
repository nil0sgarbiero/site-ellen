<script setup>
const route = useRoute()

const { data: post } = await useAsyncData(route.path, () =>
  queryCollection('blog').path(route.path).first()
)

if (!post.value) {
  throw createError({ statusCode: 404, statusMessage: 'Artigo não encontrado', fatal: true })
}

const formatarData = (data) =>
  new Date(data).toLocaleDateString('pt-BR', { timeZone: 'UTC' })

useHead({ title: `${post.value.title} — Ellen Sgarbiero` })
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

    <article class="container artigo">
      <div class="post-topo">
        <span class="categoria">{{ post.category }}</span>
        <span class="data">{{ formatarData(post.date) }}</span>
      </div>
      <h1>{{ post.title }}</h1>
      <ContentRenderer :value="post" />
      <NuxtLink to="/blog" class="voltar">← Voltar aos artigos</NuxtLink>
    </article>

    <footer>
      <img src="/img/logo.png" alt="Logo Ellen Sgarbiero">
      <p class="oab">OAB/SP 000.000</p>
      <p>© {{ new Date().getFullYear() }} Ellen Sgarbiero — Advocacia. Todos os direitos reservados.</p>
    </footer>
  </div>
</template>