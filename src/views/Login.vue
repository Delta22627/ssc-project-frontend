<template>
  <v-container fill-height >
    <template>
      <v-layout class=" align-center justify-center">

      <v-form ref="form" v-model="valid" lazy-validation>
        <h2 align="left">Login </h2>
        <v-text-field
          v-model="username"
          :counter= "20"
          :rules="usernameRules"
          label="Username"
          required
        ></v-text-field>

        <v-text-field
          type="password"
          v-model="password"
          :rules="passwordRules"
          label="Password"
          required
        ></v-text-field>

        <v-btn :disabled="!valid" color="success" class="mr-4" @click="submit"
          ><v-icon left>mdi-login-variant</v-icon>
          Login</v-btn
        >

        <v-btn color="error" class="mr-4" @click="reset">
          <v-icon left>mdi-minecraft mdi-spin</v-icon>Reset</v-btn>

      </v-form>
      </v-layout>
    </template>
  </v-container>
</template>

<script>
import Vue from "vue";

export default {
  data: () => ({
    valid: true,
    username: "",
    password: "",
    usernameRules: [(v) => !!v || "User is required"],
    passwordRules: [(v) => !!v || "Password is required"],
  }),

  methods: {
    async submit() {
      if (this.$refs.form.validate()) {
        //submit to backend to authenticate
        let formData = new FormData();
        formData.append("username", this.username);
        formData.append("password", this.password);

        let response = await Vue.axios.post("/api/login", formData);
        if (response.data.success) {
          this.$router.push({ path: "/" });
        }
      }
    },
    reset() {
      this.$refs.form.reset();
    },
  },
};
</script>
