<template>
  <v-main>
    <v-container>
      <h2>{{ locations.title }}</h2>
      <p>{{ locations.description }}</p>
      <p>Author: {{ locations.author.name }}</p>
      <p>Published on: {{ formatDate(locations.createdAt) }}</p>
      <br />
      <nuxt-content :document="locations" />
    </v-container>
  </v-main>
</template>

<script>
export default {
  async asyncData({ $content, params, error }) {
    try {
      const locations = await $content(`locations/${params.slug}`).fetch()
      return {
        locations,
      }
    } catch (e) {
      error('No locations found')
    }
  },
  methods: {
    formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString('en', options)
    },
  },
}
</script>

<style>


img {
  height: 700px;
  width: auto;
}
</style>