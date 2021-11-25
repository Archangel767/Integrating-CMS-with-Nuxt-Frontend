<template>
  <div>
    <h1>Locations</h1>
    <ul>
      <li v-for="location of locations" :key="location.slug">
        <NuxtLink :to="{ name: 'locations-slug', params: { slug: location.slug } }">
          
          <div>
            <h2>{{ location.title }}</h2>
            <p>by {{ location.author.name }}</p>
            <p>{{ location.description }}</p>
            <img :src="location.img" :alt="location.alt" />
          </div>
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const locations = await $content('locations')
      .only(['title', 'description', 'img', 'slug', 'author'])
      .sortBy('createdAt', 'asc')
      .fetch()

    return {
      locations,
    }
  },
  head() {
    return {
      script: [
        { src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' },
      ],
    }
  },
}
</script>