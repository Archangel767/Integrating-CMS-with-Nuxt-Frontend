<template>
  <v-main>
    <v-container>
      <h2>{{ article.title }}</h2>
      <p>{{ article.description }}</p>
      <p> Author: {{ article.author.name }} </p>
      <p>Published on: {{ formatDate(article.createdAt) }}</p>
      <br>
      <nuxt-content :document="article" />
    </v-container>
  </v-main>
</template>

<script>
export default {
  async asyncData({ $content, params, error }) {
    try {
      const article = await $content(`articles/${params.slug}`).fetch()
      return {
        article,
      }
    } catch (e) {
      error('No article found')
    }
  },
  methods: {
    formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString('en', options)
    }
 }
}
</script>

<style>
  img {
    height: 400px;
    width: auto;
  }
</style>