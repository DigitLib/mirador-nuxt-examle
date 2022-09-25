<template>
  <div id="iiif"></div>
</template>

<script>
import Mirador from 'mirador/dist/es/src/index'
import { miradorImageToolsPlugin } from 'mirador-image-tools'
import textOverlayPlugin from 'mirador-textoverlay'

export default {



  async asyncData({$content, params}) {
    const links = await $content("iiif", params.slug)
      .only(["title", "mnf1", "mnf2", "pg"])
      .fetch();
    // const mtd = await $content("mtd").where({ slug: { $in:post.mtd } }).fetch()
    return {
      man1: links.mnf1,
      man2: links.mnf2,
      pag: links.pg
    };
  },

  data: () => ({
    title: "Упоредни",
  }),
  head() {
    return {
       title: this.title
    };

  },

  computed: {
    miradorViewerOptions() {

      // const manifest1 = this.$route.query.mnf1
      // const manifest2 = this.$route.query.mnf2
      // const manifest1 = this.asyncData().mnf1
      // const manifest2 = this.mnf2
      // const pg = this.$route.query.pg
      // const collection = this.$route.query.col
      const color = this.$vuetify.theme.dark === false ? 'light' : 'dark'

      const config = {
        id: "iiif",
        selectedTheme: color,
        language: 'en',
        windows: [
          {
            loadedManifest: this.man1,
          },
          {
            loadedManifest: this.man2,
            canvasIndex: this.pag
          },
        ],
        // catalog: [
        //   collection
        //   ],
        window: {
          allowClose: false,
          // defaultView: 'single',
          views: [
            { key: 'single', behaviors: ['individuals'] },
            { key: 'book', behaviors: ['paged'] },
            { key: 'gallery' },
          ],
          // elastic: {
          //   height: 500,
          //   width: 600
          // },
          textOverlay: {
            enabled: true,
            // selectable: false,
            visible: false,
          },
          imageToolsEnabled: true,
        },
        workspaceControlPanel: {
          enabled: false,
        }
        // workspace: {
        //   type: 'elastic'
        // }
      }
      // Mirador.viewer(config, [...miradorImageToolsPlugin, textOverlayPlugin])
      return config;
    },
  },

  mounted() {
    this.mirador = Mirador.viewer(this.miradorViewerOptions, [...miradorImageToolsPlugin, textOverlayPlugin]);
  },

  beforeDestroy() {
    this.mirador.unmount()
  },


}
</script>
