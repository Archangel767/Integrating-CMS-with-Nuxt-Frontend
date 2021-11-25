<template>
  <div class="container">
    <AppHeader />
    <InfoBox />
    <nuxt />
    <AppFooter />
  </div>
</template>

<script>
  import AppHeader from '../components/AppHeader';
  import InfoBox from '../components/InfoBox';
  import AppFooter from '../components/AppFooter';
  export default {
    components: {
      AppHeader,
      InfoBox,
      AppFooter
    }
}
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: Arial, Helvtica, sans-serif;
    font-size: 1rem;
    line-height: 1.6;
    background: #f4f4f4
  }

  a {
    color: #666;
    text-decoration: none;
  }

  ul {
    list-style: none;
  }

.container {
  max-width: 800px;
  margin: 2rem auto;
  overflow: hidden;
}
</style>