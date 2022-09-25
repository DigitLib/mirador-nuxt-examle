<template>
  <div>
    <v-container>
      <h1 class="blog-header">Shakespeare's Books</h1>

      <div class="d-flex flex-wrap justify-center">
        <v-card
          v-for="post of posts"
          :key="post.slug"
          class="ma-5"
          tile
          max-width="400"
        >
          <NuxtLink
            class="post-card"
            :to="{ name: 'books-slug', params: { slug: post.slug } }"
          >
            <v-img
              :src="post.img" contain

            >

            </v-img>
<!--            <v-card-title>{{ post.title }}</v-card-title>-->
          </NuxtLink>
        </v-card>
      </div>
    </v-container>
  </div>
</template>

<script>

export default {
  name: "Books",
  async asyncData({ $content, params }) {
    const posts = await $content("books", params.slug)
      .only(["title", "description", "img", "slug", "mnf"])
      // .sortBy("createdAt", "asc")
      .fetch();
    return {
      posts,
    };
  },
  data: () => ({
    title: "Books",
    description: "Mirador Catalog integration",
  }),
  head() {
    return {
      title: this.title,
      meta: [
        {
          hid: "description",
          name: "description",
          content: this.description,
        },
        // Open Graph
        {
          hid: "og:title",
          property: "og:title",
          content: this.title,
        },
        {
          hid: "og:description",
          property: "og:description",
          content: this.description,
        },

      ],
    };
  },

};
</script>

<style>

</style>
