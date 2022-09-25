<template>
  <v-container>
    <v-row>
      <v-col cols="12" md="3" align-self="center">
        <v-img
          max-width="460"
          src="img/Shakespeare.jpg"
          lazy-src="img/Shakespeare.jpg"
          class="ma-auto"
          >
        </v-img>
      </v-col>
      <v-col cols="12" md="8" align-self="center">
        <h2 class="text-center pa-2">Digital Shakespeare</h2>
        <v-divider></v-divider>
        <p>This is an example of IIIF and Mirador Viewer implementation in Nuxt.js v2</p>
        <p>All content is defined in Nuxt/Content (e.g. /content dir)</p>
        <p><u>Architecture:</u></p>
        <p>Mirador Viewer is implemented in a page.</p>
        <p>IIIF Manifests are defined in MD file as Content.</p>
        <p>Viewer is built with plugins => Image Tools and TextLayer (with Serbian Translation).</p>
        <p>Run by: <a href="https://iiif.io" target="_blank"> <v-img src="img/logo/iiif-logo.png" max-width="50" title="International Image Interoperability Framework"></v-img></a><a href="https://projectmirador.org" target="_blank"><v-img src="img/logo/mirador-logo.png" max-width="50" title="Mirador IIIF Viewer"></v-img></a><a href="https://nuxtjs.org/" target="_blank"><v-img src="img/logo/nuxt-logo.svg" max-width="50" title="Nuxt.js"></v-img> </a> </p>
      </v-col>
    </v-row>
    <h3 class="mt-5 mb-5">Сontent is captured from:</h3>
    <v-row>
      <v-col
        cols="12"
        sm="4"
        md="4"
        >
        <a href="https://digital.bodleian.ox.ac.uk" target="_blank">
        <v-img src="img/logo/bodlean.jpg" max-width="200" class="ma-auto"></v-img>
        </a>
      </v-col>
      <v-col
        cols="12"
        md="4"
        sm="4"
        class="d-flex justify-center"
      >
        <a href="https://www.digitale-sammlungen.de/en" target="_blank" class="ma-auto">
        <v-img src="img/logo/bsb_logo.jpg" max-width="300"></v-img>
        </a>
      </v-col>
      <v-col
        cols="12"
        md="4"
        sm="4"
        >
        <a href="https://milutinbojic.digitalna.rs/" target="_blank">
        <v-img src="img/logo/bmb-logo.png" max-width="200" class="ma-auto"></v-img>
        </a>
      </v-col>
    </v-row>
  </v-container>
</template>
<script>
export default {

}
</script>

<style>
@media (min-width: 1264px) {
  .container {
    max-width: 90% !important;
  }
}

@media (min-width: 960px) {
  .container {
    max-width: 90% !important;
  }
}
</style>
