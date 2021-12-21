<template>
  <div>
    <h1> Bem vindo ao blognuxt</h1>
    <div
      v-for="(article, index) in articles" :key="index">
      <nuxt-link :to="`${article.slug}`">
      {{ article.title }}
      </nuxt-link>
    </div> 
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  async asyncData ({ $content }) {
  // implicit (assumes $eq operator)
    const articles = await $content().fetch()
    console.log(articles)
    return {articles}
  }
}
</script>

<style> 
  h1 {font-family: "helvetia";}
</style>
