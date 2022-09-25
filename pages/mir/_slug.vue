<template>
  <div id="iiif"></div>
</template>

<script>
import Mirador from 'mirador/dist/es/src/index'
import { miradorImageToolsPlugin } from 'mirador-image-tools'
import textOverlayPlugin from 'mirador-textoverlay'

export default {

  async asyncData({$content, params}) {
    const links = await $content("mir", params.slug)
      .only(["title", "mnf1", "pg" ])
      .fetch();
    // const mtd = await $content("mtd").where({ slug: { $in:post.mtd } }).fetch()
    return {
      man1: links.mnf1,
      pag: links.pg
      // man2: links.mnf2
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
            canvasIndex: this.pag
          },
          // {
          //   loadedManifest: this.man2,
            // canvasIndex: pg
          // },
        ],
        // catalog: [
        //   collection
        //   ],
        window: {
          allowClose: false,
          views: [
            { key: 'single' },
            { key: 'book' },
            { key: 'gallery' },
          ],
          // defaultView: 'single',
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

  // methods: {
  //   render() {
  //     this.render = false
  //     this.$nextTick(() => {
  //       this.render = true
  //     });
  //   },

    beforeDestroy() {
      this.mirador.unmount()
    }

    // this.$nextTick(() => {
    //   this.mirador = Mirador.viewer(this.miradorViewerOptions, [...miradorImageToolsPlugin, textOverlayPlugin]);
    // })


}
</script>
