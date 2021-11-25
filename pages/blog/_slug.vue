<template>
  <div>
    <article>
    <nuxt-content :document="article" />
    <pre> {{ article }} </pre>

  </article>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const article = await $content('articles', params.slug).fetch()

    return { article }
  }
}
</script>

<style>

</style>