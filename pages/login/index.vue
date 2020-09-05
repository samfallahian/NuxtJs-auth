<template>
  <v-container class="fill-height" fluid>
    <v-row align="center" justify="center">
      <v-col cols="12" sm="8" md="4">
        <v-form @submit.prevent="login">
          <v-card class="elevation-12">
            <v-toolbar color="primary" dark flat>
              <v-toolbar-title>Login form</v-toolbar-title>
              <v-spacer></v-spacer>
            </v-toolbar>
            <v-card-text>
              <v-text-field
                label="Username"
                name="username"
                v-model="username"
                prepend-icon="mdi-account"
                type="text"
              ></v-text-field>

              <v-text-field
                id="password"
                label="Password"
                v-model="password"
                name="password"
                prepend-icon="mdi-lock"
                type="password"
              ></v-text-field>
            </v-card-text>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn type="submit" color="primary">Login</v-btn>
            </v-card-actions>
          </v-card>
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  layout: "login",
  auth: "guest",
  data() {
    return {
      username: "",
      password: "",
    };
  },
  methods: {
    login() {
      this.$auth
        .loginWith("local", {
          data: {
            username: this.username,
            password: this.password,
          },
        })
        .then((resp) => {
          this.$auth.setToken(
            "local",
            "Bearer " + resp.data.result.access_token
          );
          this.$auth.setRefreshToken("local", resp.data.result.refresh_token);
          this.$axios.setHeader(
            "Authorization",
            "Bearer " + resp.data.result.access_token
          );
          this.$auth.ctx.app.$axios.setHeader(
            "Authorization",
            "Bearer " + resp.data.result.access_token
          );
          this.$auth.setUser(resp.data.result.user);
          // this.$router.push("/");
        })
        .catch((err) => {
          if (err.response) {
            console.log(err.response);
          }
        });
    },
  },
};
</script>