<template>
  <v-container>
    <NuxtLink :to="`/books`" class="blog-list-link">
      <v-icon>mdi-arrow-left</v-icon></NuxtLink>
    <h1 class="blog-title mb-10">{{ post.title }}</h1>

    <h4 class="blog-description">{{ post.description }}</h4>
    <v-row>
      <v-col cols="12" md="6">
        <v-img :src="post.img" class="grey lighten-2" max-width="400"> </v-img>
        <h3 class="mt-5">View</h3>
        <NuxtLink :to="post.mnf">
          <v-img src="img/logo/mirador-logo.png" max-width="60" class="mt-5 mb-5"></v-img>
        </NuxtLink>
        <nuxt-content :document="mtd" />
       <a :href="mtd.src" target="_blank">
        <v-img :src="mtd.img" class="mt-3" max-width="200"></v-img>
       </a>
       <h1>Licence:</h1>
       <a :href="mtd.llnk" target="_blank">
         <v-img :src="mtd.limg" class="mt-3" max-height="35" max-width="210"></v-img>
       </a>
      </v-col>
      <v-col cols="12" md="6">
         <nuxt-content :document="post" />
      </v-col>
    </v-row>

  </v-container>
</template>

<script>
export default {

  name: "PageSlug",

  async asyncData({ $content, params }) {
    const post = await $content("books", params.slug).fetch();
    const mtd = await $content("mtd", params.slug).fetch();
    // const mtd = await $content("mtd").where({ slug: { $in:post.mtd } }).fetch()
    return { post, mtd };
  },

  head() {
    return {
      title: this.post.title,
      titleTemplate: "%s - Шекспир",
      meta: [
        {
          hid: "description",
          name: "description",
          content: this.post.description,
        },
        // Open Graph
        { hid: "og:title", property: "og:title", content: this.post.title },
        {
          hid: "og:description",
          property: "og:description",
          content: this.post.description,
        },
        { hid: "og:type", property: "og:type", content: "article" },


      ],
    };
  },

};
</script>

<style>
@media (min-width: 960px) {
  .container {
    max-width: 90% !important;
  }
}

.blog-title {
  font-size: 48px;
  font-weight: 400;
}

@media only screen and (max-width: 600px) {
  .blog-title {
    font-size: 36px;
  }
}

.blog-description {
  font-weight: 400;
  font-style: italic;
}

.nuxt-content h2 {
  font-weight: 500;
  font-size: 30px;
  padding-bottom: 0.3rem;
  /*border-bottom: 1px solid #eaecef;*/
  margin-bottom: 1rem;
}

.nuxt-content h3 {
  font-weight: 400;
  font-size: 22px;
}

.nuxt-content p {
  font-size: 16px;
  margin-bottom: 30px;
  word-spacing: 2px;
  line-height: 32px;
}

.nuxt-content p code,
.nuxt-content h2 code,
.nuxt-content h3 code {
  color: #476582;
  padding: 0.25rem 0.5rem;
  margin: 0;
  font-size: 0.85em;
  background-color: rgba(27, 31, 35, 0.05);
  border-radius: 3px;
  font-family: Consolas, Roboto Mono, monospace;
}

.nuxt-content ul {
  font-size: 16px;
  margin-bottom: 30px;
  word-spacing: 2px;
  line-height: 32px;
  display: block;
  list-style-type: disc;
  margin-block-start: 1em;
  margin-block-end: 1em;
  margin-inline-start: 0px;
  margin-inline-end: 0px;
  padding-inline-start: 40px;
}

.nuxt-content summary {
  font-size: larger;
}

</style>
