<template>
  <v-app id="inspire">
    <AppBar />
    <Snackbar></Snackbar>
    <v-main>
      <v-container class="fill-height" fluid>
        <nuxt />
      </v-container>
    </v-main>
    <Footer />
  </v-app>
</template>

<script>
import AppBar from "~/components/Partial/AppBar";
import Footer from "~/components/Partial/Footer";
export default {
  components: {
    AppBar,
    Footer,
  },

  data: () => ({}),
};
</script>