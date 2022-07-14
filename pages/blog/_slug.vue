<template>
  <v-card>
    <article>
        <h1 class="text-h2">{{article.title}}</h1>
        <p class="font-weight-light">{{article.description}}</p>
        <nuxt-content :document="article" />
    </article>
  </v-card>
</template>

<script>
export default {
    async asyncData({ $content, params }) {
        const article = await $content('article', params.slug).fetch();
        return { article }
    }
}
</script>

<style>
article {
  display: block;
  margin: 0 auto;
  padding: 50px 30px;
  max-width: 800px;
}
h1 {
  font-size: 28px;
  font-weight: 900;
  margin-bottom: 30px;
}
</style>