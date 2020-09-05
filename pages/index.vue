<template>
  <v-row align="center" justify="center">
    <v-btn @click="logout">Logout</v-btn>
  </v-row>
</template>

<script>
export default {
  components: {},
  methods: {
    logout() {
      this.$auth.logout().then((data) => {
        console.log("logout");
      });
    },
  },
};
</script>
