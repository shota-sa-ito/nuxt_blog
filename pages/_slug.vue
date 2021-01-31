<template>
  <article class="container mx-auto my-8 px-20 md:px-0">
    <h1 class="text-3xl font-bold my-8">{{ article.title || '' }}</h1>
    <div class="markdown-body">
      <nuxt-content class="markdown-body" :document="article" />
    </div>
  </article>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const query = $content('articles', params.slug)
    const article = await query.fetch()
    return { article }
  }
}
</script>

<style>
@import url("../node_modules/github-markdown-css/github-markdown.css");

.markdown-body ul {
    list-style: disc;
}

.markdown-body ol {
    list-style: decimal;
}
</style>