<template>
  <div class="container mx-auto my-8">
    <Card v-for="(article, index) in articles" :key="index" :title="article.title" :date="article.date" :summary="article.summary" :category="article.category" :slug="article.slug" />
  </div>
</template>

<script>
import Card from '~/components/Card'

export default {
  async asyncData({ $content }) {
    const query = await $content('articles').limit(15)
    const articles = await query.fetch()
    return { articles }
  }
}
</script>