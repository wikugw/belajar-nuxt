<template>
  <div class="container">
    <div>
      <Logo />
      <h1 class="title">
        nuxt-fundamentals
      </h1>
      <div class="links">
        <a
          href="https://nuxtjs.org/"
          target="_blank"
          rel="noopener noreferrer"
          class="button--green"
        >
          Documentation
        </a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          rel="noopener noreferrer"
          class="button--grey"
        >
          GitHub
        </a>
      </div>
    </div>

    <div class="links">
      <nuxt-link
        v-for="post in posts"
        :key="post.id"
        :to="{name: 'posts-id', params: {id: post.id}}"
        class="button-grey"
      >
        {{post.title}}
      </nuxt-link>
    </div>
  </div>
</template>

<script>
  export default {
    head() {
      return {
        title: 'homepage 🙏',
            meta: [
                {name: 'twitter:title', content: 'nuxt'},
                {name: 'twitter:description', content: 'belajar nuxt'},
                {name: 'twitter:image', content: 'https://upload.wikimedia.org/wikipedia/en/thumb/7/78/Scum_Fuck_Flower_Boy_alt_cover.jpg/220px-Scum_Fuck_Flower_Boy_alt_cover.jpg'},
                {name: 'twitter:card', content: 'summary_large_image'},
            ]
      }
    },
    computed: {
      posts () {
        return this.$store.state.posts.all
      }
    }
  }
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
