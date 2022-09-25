<template>
  <div>
    <v-container>
      <h1 class="blog-header">About</h1>
      <v-row>
        <v-col>
          <v-img
            class="pa-2"
            src="img/Shakespeare.jpg"
            width="231"
            height="290"

          >
          </v-img>
        </v-col>

        <v-spacer></v-spacer>

        <v-col class="justify-end">
          <v-img
            class="pa-2 ml-auto"
            src="img/bojic.jpg"
            width="231"
            height="290"

          ></v-img>
        </v-col>
      </v-row>

      <br>

      <div class="d-flex flex-wrap justify-left">
        <p>The main challenge was to call exact title from different sources in a single viewer using IIIF.</p>
        <p>"First Folio" (Beineke Library) is a single book edition of Shakespeare's dramas, while other sources are divided either as single (Serbian) or collected (English) dramas.
        <p>Sources used in this project:<br>- Bodleian => First Folio (1 Book)<br>- Bavarian => Macmillan (9 volumes), Routhledge (3 volumes) - Search and Select Text<br>- "Milutin Bojic" Library => Српски (Translations on Serbian) - Search and Select Text.</p>
        <p>COMPARABLE uses a single /iiif/_slug.vue page for a viewer, Mirador, while the data is defined in .md files in /content/iiif. This approach, simplyfies data distriution which define composition of a viewer</p>
        <p>DROP IN allow Drag and Drop manifest link, just grab the link from dropdown menu and drop it in a viewer.</p>
        <p>VIEW ALL is a page with a Mirador viewer with defined catalog. Open a panel with all available Shakespeare's works.</p>
        <p>BOOKS is created as a blog page while books are created as a post. Used a _slug <a href="https://nuxtjs.org/examples/routing/dynamic-pages/" target="_blank"> Nuxt Dynamic Page</a>.</p>
      </div>
    </v-container>
  </div>
</template>

<script>

export default {
  name: "About",

  data: () => ({
    title: "About",
    description: "Read more about this implementation",
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

<style >
.blog-header {
  text-align: center;
  margin-top: 15px;
  margin-bottom: 30px;
  font-weight: 400;
}
.post-card {
  font-size: 1.3em !important;
  text-align: center !important;
}
.theme--dark.v-card > .v-card__text {
  color: white !important;
}

</style>
