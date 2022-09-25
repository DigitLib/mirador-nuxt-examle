<template>

          <NuxtLink
            :to="{ name: 'iiif-slug', params: { slug: link.slug } }"
          >
          </NuxtLink>

</template>

<script>

export default {
  name: "Iiif",
  async asyncData({ $content, params }) {
    const link = await $content("iiif", params.slug)
      .only(["title", "mnf1", "mnf2", "slug" ])
      // .sortBy("createdAt", "asc")
      .fetch();
    return {
      link,
    };
  },
  data: () => ({
    title: "Књиге - Шекспир",
    description: "Доступна дигитална издања",
  }),
  // head() {
  //   return {
  //     title: this.title,
  //     meta: [
  //       {
  //         hid: "description",
  //         name: "description",
  //         content: this.description,
  //       },
  //       // Open Graph
  //       {
  //         hid: "og:title",
  //         property: "og:title",
  //         content: this.title,
  //       },
  //       {
  //         hid: "og:description",
  //         property: "og:description",
  //         content: this.description,
  //       },
  //
  //     ],
  //   };
  // },

};
</script>

<style>
/*.blog-header {*/
/*  text-align: center;*/
/*  margin-top: 15px;*/
/*  margin-bottom: 30px;*/
/*  font-weight: 400;*/
/*}*/
/*.post-card {*/
/*  text-decoration: none;*/
/*}*/
/*.read-more {*/
/*  color: rgb(92, 148, 252);*/
/*}*/
</style>
