
<template> 
    <div>
        <v-card elevation="2" outlined shaped>
            <h1 class="text-center text-h1">News</h1>
            <p class="text-center">このサービスの新機能やお知らせを不定期で更新していきます。</p>
            <p class="text-center font-weight-light">*記事は予告なしに削除されたり、非公開になる場合があります。</p>
        </v-card>
        <br>
        <div v-for="article in articles" :key="article.slug">
            <v-card max-width=800 class="mx-auto pa-6">
                <nuxt-link :to="'blog/' + article.slug">
                    <h2 class="text-center text-h3">{{article.title}}</h2>
                </nuxt-link>
                <p class="text-center">{{article.description}}</p>
            </v-card>
            <br>
        </div>
        
    </div>
</template>
<script>
    export default{
            name:"BlogIndex",
            async asyncData({ $content }) {
                const articles = await $content('article').fetch();
                return { articles }
        }
    }
</script>