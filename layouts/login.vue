<template>
  <v-app id="inspire">
    <Snackbar></Snackbar>
    <v-main>
      <nuxt />
    </v-main>
  </v-app>
</template>

<script>
export default {
  props: {
    source: String,
  },
};
</script>