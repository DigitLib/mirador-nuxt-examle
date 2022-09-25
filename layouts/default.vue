<template>
  <v-app dark>
    <siteHeader />
    <v-main>
      <v-container>
        <Nuxt />
<!--         <Nuxt :key="$route.fullPath"></Nuxt>-->
      </v-container>
    </v-main>
    <v-footer app>
      <span>&copy; {{ new Date().getFullYear() }} DigitLib</span>
      <v-spacer></v-spacer>
      <v-icon>{{
          $vuetify.theme.dark ? 'mdi-github' : 'mdi-github'
        }}</v-icon>
    </v-footer>
  </v-app>
</template>
<script>
import siteHeader from "~/components/siteHeader";
export default {


}
</script>

