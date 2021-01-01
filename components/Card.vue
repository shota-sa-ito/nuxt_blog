<template>
  <nuxt-link :to="slug">
    <article class="border p-4 rounded my-4">
        <h2 class="text-xl font-bold">{{ title }}</h2>
        <time class="text-right text-sm text-gray-700">{{ date }}</time>
        <p class="mt-4 text-sm text-gray-700 leading-loose">{{ summary }}</p>
        <div class="tags"><Tag v-for="(category, index) in categorys" :key="index">{{ category }}</Tag></div>
    </article>
  </nuxt-link>
</template>

<script>
import Tag from '~/components/Tag'

export default {
  props: {
    title: String,
    date: String,
    summary: String,
    category: String,
    slug: String
  },
  computed: {
    categorys() {
      if (!this.category) {
          return null
      }

      return this.category.split(' ')
    }
  }
}
</script>

<style>

</style>