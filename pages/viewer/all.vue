<template>
  <div id="iiif"></div>
</template>
<script>
import Mirador from 'mirador/dist/es/src/index'
import { miradorImageToolsPlugin } from 'mirador-image-tools'
import textOverlayPlugin from 'mirador-textoverlay'

export default {

  data: () => ({
    title: "View All",
  }),
  head() {
    return {
       title: this.title
    };

  },

  computed: {
    miradorViewerOptions() {

      const color = this.$vuetify.theme.dark === false ? 'light' : 'dark'

      const config = {
        id: "iiif",
        // selectedTheme: 'dark',
        // selectedTheme: colors,
        selectedTheme: color,
        language: 'en',
        windows: [],
        catalog: [
          {
            manifestId: 'https://milutinbojic.digitalna.rs/iiif/api/presentation/3/collection/f77afd7c-334c-4c96-b962-b58775ca5044',
            provider: "Библиотека МИЛУТИН БОЈИЋ"
          },
          {
            manifestId: 'https://iiif.bodleian.ox.ac.uk/iiif/manifest/390fd0e8-9eae-475d-9564-ed916ab9035c.json',
            provider: "Digital Bodleian Library"
          },
          {
            manifestId: 'https://api.digitale-sammlungen.de/iiif/presentation/v2/bsb10749560/manifest',
            provider: "Bayerische Staatsbibliothek"
          },
          {
            manifestId: 'https://api.digitale-sammlungen.de/iiif/presentation/v2/bsb10749561/manifest',
            provider: "Bayerische Staatsbibliothek"
          },
          {
            manifestId: 'https://api.digitale-sammlungen.de/iiif/presentation/v2/bsb10749562/manifest',
            provider: "Bayerische Staatsbibliothek"
          },
          {
            manifestId: 'https://api.digitale-sammlungen.de/iiif/presentation/v2/bsb10749563/manifest',
            provider: "Bayerische Staatsbibliothek"
          },
          {
            manifestId: 'https://api.digitale-sammlungen.de/iiif/presentation/v2/bsb10749564/manifest',
            provider: "Bayerische Staatsbibliothek"
          },
          {
            manifestId: 'https://api.digitale-sammlungen.de/iiif/presentation/v2/bsb10749565/manifest',
            provider: "Bayerische Staatsbibliothek"
          },
          {
            manifestId: 'https://api.digitale-sammlungen.de/iiif/presentation/v2/bsb10749566/manifest',
            provider: "Bayerische Staatsbibliothek"
          },
          {
            manifestId: 'https://api.digitale-sammlungen.de/iiif/presentation/v2/bsb10749567/manifest',
            provider: "Bayerische Staatsbibliothek"
          },
          {
            manifestId: 'https://api.digitale-sammlungen.de/iiif/presentation/v2/bsb10749568/manifest',
            provider: "Bayerische Staatsbibliothek"
          },
          {
            manifestId: 'https://api.digitale-sammlungen.de/iiif/presentation/v2/bsb11021855/manifest',
            provider: "Bayerische Staatsbibliothek"
          },
          {
            manifestId: 'https://api.digitale-sammlungen.de/iiif/presentation/v2/bsb11021856/manifest',
            provider: "Bayerische Staatsbibliothek"
          },
          {
            manifestId: 'https://api.digitale-sammlungen.de/iiif/presentation/v2/bsb11021857/manifest',
            provider: "Bayerische Staatsbibliothek"
          },
          {
            manifestId: 'https://milutinbojic.digitalna.rs/iiif/api/presentation/3/a7dffa27-9e1d-44ff-9ac9-0091400891d2%252F00000001%252Fbojicbib%252F00000008/manifest',
            provider: "Библиотека МИЛУТИН БОЈИЋ"
          },
          // collection
        ],

        window: {
          // allowClose: false,
          // defaultView: 'single',
          views: [
            { key: 'single' },
            { key: 'book' },
            { key: 'gallery' },
          ],
          textOverlay: {
            enabled: true,
            // selectable: false,
            visible: false,
          },
          imageToolsEnabled: true,
        },
        workspace: {
          isWorkspaceAddVisible: true
        }
      }
      // Mirador.viewer(config, [...miradorImageToolsPlugin, textOverlayPlugin])
      return config;
    },
  },

  mounted() {
    // this.$nextTick(() => {
    //     this.mirador = Mirador.viewer(this.miradorViewerOptions, [...miradorImageToolsPlugin, textOverlayPlugin]);
    //   })
    this.mirador = Mirador.viewer(this.miradorViewerOptions, [...miradorImageToolsPlugin, textOverlayPlugin]);
  },

  beforeDestroy() {
    this.mirador.unmount()
  },


}
</script>

<style>

.v-navigation-drawer {
  z-index: 1200;
}
</style>
