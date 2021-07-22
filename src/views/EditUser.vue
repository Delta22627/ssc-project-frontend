<template>
  <v-container>
    <div class="EditUser">
      <h1>Edit User {this.username} Password</h1>
    </div>
    <template>
      <v-form ref="form" v-model="valid" lazy-validation>
        <v-text-field
          v-model="username"
          :rules="usernameRules"
          label="Input username"
          required
        ></v-text-field>

        <v-text-field
          type="password"
          v-model="password"
          :rules="passwordRules"
          label="Enter your current password"
          required
        ></v-text-field>

        <v-text-field
          type="password"
          v-model="newPassword"
          :rules="newPasswordRules"
          label="Please enter your new password"
          required
        ></v-text-field>

        <v-btn :disabled="!valid" color="primary" class="mr-4" @click="submit"
          ><v-icon left>mdi-check</v-icon>confirm</v-btn
        >
        <v-btn :disabled="!valid" color="error" class="mr-4" @click="reset"
          ><v-icon left>mdi-close-circle</v-icon>reset</v-btn
        >
      </v-form>
    </template>
  </v-container>
</template>

<script>
import Vue from "vue";

export default {
  data: () => ({
    valid: true,
    username: "",
    newPassword: "",
    password: "",
    usernameRules: [(v) => !!v || "Username cannot be blank"],
    newPasswordRules: [(v) => !!v || "Password cannot be blank"],
    passwordRules: [(v) => !!v || "Password is required"],
  }),

  methods: {
    async submit() {
      if (this.$refs.form.validate()) {
        //submit to backend to authenticate

        let response = await Vue.axios.post("/api/user", {
          username: this.username,
          password: this.newPassword,
        });
        console.log(response);
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
