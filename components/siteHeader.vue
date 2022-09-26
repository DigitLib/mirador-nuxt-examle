<template>
  <div>
    <v-navigation-drawer v-model="drawer" fixed app temporary>
      <v-list flat>
        <v-list-item to="/books" class="text-uppercase">
          <v-list-item-title>Books</v-list-item-title>
        </v-list-item>
        <v-list-item to="/viewer/all" class="text-uppercase">
          <v-list-item-title>Review All</v-list-item-title>
        </v-list-item>
        <v-list-item-group>
          <v-list-group>
           <template #activator>
              <v-list-item-title class="text-uppercase">
                Comparable
              </v-list-item-title>
            </template>

            <v-list>
              <v-list-group
                v-for="item in items"
                :key="item.title"
                :prepend-icon="item.action"
                no-action
              >
                <template #activator>
                  <v-list-item>
                    <v-list-item-content>
                      <v-list-item-title>{{ item.title }}</v-list-item-title>
                    </v-list-item-content>
                  </v-list-item>
                </template>

                <v-list-item
                  v-for="subItem in item.items"
                  :key="subItem.title"
                  route :to="subItem.link"
                  target="_top"
                >
                  <v-list-item-content>
                    <v-list-item-title>{{ subItem.title }}</v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
              </v-list-group>
            </v-list>
          </v-list-group>
        </v-list-item-group>
        <v-list-item to="/about" class="text-uppercase">
          <v-list-item-title>About</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar fixed flat app>
      <v-app-bar-nav-icon class="hidden-md-and-up" @click="drawer = true" />
      <nuxt-link to="/" class="d-flex">
        <Logo />
      </nuxt-link>
      <v-spacer />
      <v-btn to="/books" class="nav-button hidden-sm-and-down" text>Books</v-btn>
      <v-btn to="/viewer/all" class="nav-button  hidden-sm-and-down" text>View all</v-btn>
      <v-menu :close-on-content-click="false" open-on-hover offset-y>
        <template #activator="{ on, attrs }">
          <v-btn
            text
            v-bind="attrs"
            class="hidden-sm-and-down"
            v-on="on"
          >
            Comparable
          </v-btn>
        </template>

        <v-list>
          <v-list-group
            v-for="item in items"
            :key="item.title"
            :prepend-icon="item.action"
            no-action
          >
            <template #activator>
              <v-list-item>
                <v-list-item-content>
                  <v-list-item-title>{{ item.title }}</v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </template>

            <v-list-item
              v-for="subItem in item.items"
              :key="subItem.title"
              route :to="subItem.link"
              target="_top"
            >
              <v-list-item-content>
                <v-list-item-title>{{ subItem.title }}</v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list-group>
        </v-list>
      </v-menu>

      <v-menu :close-on-content-click="false" open-on-hover offset-y>
        <template #activator="{ on, attrs }">
          <v-btn
            text
            v-bind="attrs"
            class="hidden-sm-and-down"
            v-on="on"
          >
            Drop In
          </v-btn>
        </template>

        <v-list>
          <v-list-group
            v-for="item in ubaci"
            :key="item.title"
            :prepend-icon="item.action"
            no-action
          >
            <template #activator>
              <v-list-item>
                <v-list-item-content>
                  <v-list-item-title>{{ item.title }}</v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </template>

            <v-list-item
              v-for="subItem in item.naslov"
              :key="subItem.title"
              route :to="subItem.link"
              target="_top"
            >
              <v-list-item-content>
                <v-list-item-title>{{ subItem.title }}</v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list-group>
        </v-list>
      </v-menu>
<!--      <v-btn to="/bojic" class="nav-button hidden-sm-and-down" text>... and Bojic</v-btn>-->
      <v-btn to="/about" class="nav-button hidden-sm-and-down" text>About</v-btn>
      <v-spacer></v-spacer>

      <v-btn icon @click="changeThemeColor">
        <v-icon>{{
            $vuetify.theme.dark ? 'mdi-white-balance-sunny' : 'mdi-weather-night'
          }}</v-icon>
      </v-btn>
    </v-app-bar>
  </div>
</template>

<script>
export default {
  components: {},


  data: () => ({
    clipped: false,
    drawer: false,

    ubaci: [
      {
        title: "Српски",
        naslov: [
          {
            title: "The Winter's Tale",
            link: "?manifest=https://milutinbojic.digitalna.rs/iiif/api/presentation/3/f77afd7c-334c-4c96-b962-b58775ca5044%25252F00000001%25252Fvilijam1%25252F00000005/manifest"
          },
          {
            title: "Ромео и Јулија",
            link: "?manifest=https://milutinbojic.digitalna.rs/iiif/api/presentation/3/f77afd7c-334c-4c96-b962-b58775ca5044%25252F00000001%25252Fvilijam1%25252F00000006/manifest"
          },
          {
            title: "Macbeth",
            link: "?manifest=https://milutinbojic.digitalna.rs/iiif/api/presentation/3/f77afd7c-334c-4c96-b962-b58775ca5044%25252F00000001%25252Fvilijam1%25252F00000006/manifest"
          },
          {
            title: "Hamlet",
            link: "?manifest=https://milutinbojic.digitalna.rs/iiif/api/presentation/3/f77afd7c-334c-4c96-b962-b58775ca5044%25252F00000001%25252Fvilijam1%25252F00000004/manifest"
          },
          {
            title: "Julius Cæsar",
            link: "?manifest=https://milutinbojic.digitalna.rs/iiif/api/presentation/3/f77afd7c-334c-4c96-b962-b58775ca5044%25252F00000001%25252Fvilijam1%25252F00000002/manifest"
          },
          {
            title: "King Richard III",
            link: "?manifest=https://milutinbojic.digitalna.rs/iiif/api/presentation/3/f77afd7c-334c-4c96-b962-b58775ca5044%25252F00000001%25252Fvilijam1%25252F00000007/manifest"
          },
          {
            title: "Краљ Рикард III",
            link: "?manifest=https://milutinbojic.digitalna.rs/iiif/api/presentation/3/f77afd7c-334c-4c96-b962-b58775ca5044%25252F00000001%25252Fvilijam1%25252F00000001/manifest"
          },
        ]
      },
      {
        title: "English",
        naslov: [
          {
            title: "Bodleian",
            link: "/?manifest=https://iiif.bodleian.ox.ac.uk/iiif/manifest/390fd0e8-9eae-475d-9564-ed916ab9035c.json"
          }
        ]
      },

    ],
    josh: [{
      title: "test 2",
      link: "/?manifest=mnf/rout3.json"
    }],
    items: [
      {
        title: 'The Winter\'s Tale',
        items: [
          {
            title: 'Српски + Bodleian',
            link: "/iiif/zimskab"
          },
          {
            title: 'Српски + Macmillan',
            link: "/iiif/zimskam"
          },
          {
            title: 'Српски + Routledge',
            link: "/iiif/zimskar"
          }
        ]
      },
      {
        title: 'Romeo and Juliet',
        items: [
          {
            title: 'Српски + Bodleian',
            link: "/iiif/romeob"
          },
          {
            title: 'Српски + Macmillan',
            link: "/iiif/romeom"
          },
          {
            title: 'Српски + Routledge',
            link: "/iiif/romeor"
          }
        ]
      },
      {
        title: 'Macbeth',
        items: [
          {
            title: 'Српски + Bodleian',
            link: "/iiif/makbetb"
          },
          {
            title: 'Српски + Macmillan',
            link: "/iiif/makbetm"
          },
          {
            title: 'Српски + Routledge',
            link: "/iiif/makbetr"
          }
        ]
      },
      {
        title: 'Hamlet',
        items: [
          {
            title: 'Српски + Bodleian',
            link: "/iiif/hamletb"
          },
          {
            title: 'Српски + Macmillan',
            link: "/iiif/hamletm"
          },
          {
            title: 'Српски + Routledge',
            link: "/iiif/hamletr"
          }
        ]
      },
      {
        title: 'Julius Cæsar',
        items: [
          {
            title: 'Српски + Bodleian',
            link: "/iiif/cezarb"
          },
          {
            title: 'Српски + Macmillan',
            link: "/iiif/cezarm"
          },
          {
            title: 'Српски + Routledge',
            link: "/iiif/cezarr"
          }
        ]
      },
      {
        title: 'King Richard III',
        items: [
          {
            title: 'Српски + Bodleian',
            link: "/iiif/richardb"
          },
          {
            title: 'Српски + Macmillan',
            link: "/iiif/richardm"
          },
          {
            title: 'Српски + Routledge',
            link: "/iiif/richardr"
          }
        ]
      },
      {
        title: 'Краљ Рикард III',
        items: [
          {
            title: 'Српски + Bodleian',
            link: "/iiif/tristab"
          },
          {
            title: 'Српски + Macmillan',
            link: "/iiif/tristam"
          },
          {
            title: 'Српски + Routledge',
            link: "/iiif/tristar"
          }
        ]
      }
    ]


  }),
  methods: {
    changeThemeColor() {
      this.$vuetify.theme.dark = this.$vuetify.theme.dark !== true;
    },
  },
}
</script>

<style scoped>

</style>
