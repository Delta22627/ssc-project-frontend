<template>
  <v-container>
    <div class="EditUser">
      <h1> Edit User {username}</h1>
    </div>
    <template>
      <v-form ref="form" v-model="valid" lazy-validation>

        <v-text-field
            v-model="firstname"
            :rules="usernameRules"
            label="Firstname"
            required
        ></v-text-field>

        <v-text-field
            v-model="lastname"
            :rules="usernameRules"
            label="Lastname"
            required
        ></v-text-field>

        <v-text-field
            v-model="dateofbirth"
            :rules="usernameRules"
            label="Date of Birth"
            required
        ></v-text-field>

        <v-text-field
            type="password"
            v-model="password"
            :rules="passwordRules"
            label="Type your password to confirm change"
            required
        ></v-text-field>

        <v-btn :disabled="!valid" color="primary" class="mr-4" @click="submit">confirm</v-btn>
        <v-btn :disabled="!valid" color="red" class="mr-4" @click="reset">cancel</v-btn>

      </v-form>
    </template>
  </v-container>
</template>

<script>
import Vue from "vue";

export default {
  data: () => ({
    valid: true,
    firstname: "",
    lastname: "",
    password: "",
    dateofbirth: "",
    usernameRules: [(v) => !!v || "User is required"],
    passwordRules: [(v) => !!v || "Password is required"],
  }),

  methods: {
    async submit() {
      if (this.$refs.form.validate()) {
        //submit to backend to authenticate

        let response = await Vue.axios.post("/api/user", {
          username: this.username,
          firstName: this.firstname,
          lastName: this.lastname,
          dateOfBirth: this.dateofbirth,
          password: this.password,
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
