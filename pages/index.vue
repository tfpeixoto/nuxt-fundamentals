<template>
  <section class="container">
    <div>
      <logo />
      <h1 class="title">nuxt-fundamentals</h1>
      <h2 class="subtitle">My gnarly Nuxt.js project</h2>
      <div class="links">
        <nuxt-link
          v-for="post in posts"
          :to="{ name: 'posts-id', params: { id: post.id } }"
          :key="post.id"
          class="button--gray"
          >{{ post.title }}</nuxt-link
        >
      </div>
    </div>
  </section>
</template>

<script>
import Logo from "~/components/NuxtLogo.vue";
export default {
  components: {
    Logo,
  },
  head() {
    return {
      title: "Home Page",
      meta: [
        { name: "twitter:title", content: "Home page" },
        { name: "twitter:description", content: "Meu site" },
        {
          name: "twitter:image",
          content: "https://vueschool.io/img/favicons/apple-touch-icon.png",
        },
        { name: "twitter:card", content: "summary_large_image" },
      ],
    };
  },
  computed: {
    posts() {
      return this.$store.state.posts.all;
    },
  },
};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  letter-spacing: 1px;
}
.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
}
.links {
  padding-top: 15px;
}

.button--gray {
  border: 1px solid gray;
  display: inline-block;
  padding: 0.5rem 1rem;
  margin: 0 0.25rem;
  border-radius: 4px;
}
</style>
