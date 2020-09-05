<template>
  <v-snackbar v-model="show" :color="color">
    <v-row justify="space-between" align="center">
      <v-col>{{ message }}</v-col>
      <v-btn text @click="show = false">Close</v-btn>
    </v-row>
  </v-snackbar>
</template>

<script>
export default {
  data() {
    return {
      show: false,
      message: "",
      color: "",
    };
  },

  created() {
    this.$store.subscribe((mutation, state) => {
      if (mutation.type === "snackbar/showMessage") {
        this.message = state.snackbar.content;
        this.color = state.snackbar.color;
        this.show = true;
      }
    });
  },
};
</script>