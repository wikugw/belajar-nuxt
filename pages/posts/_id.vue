<template>
    <div class="container">
        <article>
            <h1 class="title">{{post.title}}</h1>
            <p>{{post.content}}</p>
        </article>
        <aside>
            <h3>Posts you might like</h3>
            <ul>
                <li v-for="related in relatedPosts" :key="related.id">
                    <nuxt-link :to="{name: 'posts-id', params: {id: related.id}}">
                        {{related.title}}
                    </nuxt-link>
                </li>
            </ul>
        </aside>
    </div>
</template>

<script>
export default {
    head () {
        return {
            title: this.post.title,
            meta: [
                {name: 'twitter:title', content: this.post.title},
                {name: 'twitter:description', content: this.post.content},
                {name: 'twitter:image', content: 'https://upload.wikimedia.org/wikipedia/en/thumb/7/78/Scum_Fuck_Flower_Boy_alt_cover.jpg/220px-Scum_Fuck_Flower_Boy_alt_cover.jpg'},
                {name: 'twitter:card', content: 'summary_large_image'},
            ]
        }
    },
    data () {
        return {
            id: this.$route.params.id
        }
    },
    computed: {
        post () {
            return this.$store.state.posts.all.find(post => post.id === this.id)
        },
        relatedPosts () {
            return this.$store.state.posts.all.filter(post => post.id !== this.id)
        }
    }

}
</script>

<style scoped>
    .container {
        display: flex;
        justify-content: space-between;
        line-height: 1.5;
    }
    article * {
        margin-bottom: 1 rem;
    }
    aside {
        min-width: 280px;
        max-width: 280px;
    }
</style>