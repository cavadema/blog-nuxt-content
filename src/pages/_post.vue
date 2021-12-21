<template>
  <div>
    <h1> {{ article.title }} </h1>
    <nuxt-content :document="article" />
  </div>
</template>

<script>
export default {
  name: 'PostPage',
  async asyncData ( context ) {
   const articles = await context.$content()
      .where({ slug: context.params.post })
      .fetch()
   return { article:articles[0] }
  },
  head () {
    return { title:this.article.title,meta:[{name:"description",content:this.article.description }] }
  }

}
</script>

<style> 
  h1 {font-family: "helvetia";}
</style>
