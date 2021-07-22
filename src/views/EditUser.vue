<template>
  <v-container>
    <div class="EditUser">
      <h1> Edit User {this.username} </h1>
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
            :rules="lastnameRules"
            label="Lastname"
            required
        ></v-text-field>

        <v-text-field
            v-model="dateofbirth"
            :rules="dateofbirthRules"
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


        <v-btn :disabled="!valid" color="primary" class="mr-4" @click="submit"><v-icon left>mdi-check</v-icon>confirm</v-btn>
        <v-btn :disabled="!valid" color="error" class="mr-4" @click="reset"><v-icon left>mdi-close-circle</v-icon>reset</v-btn>

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
    usernameRules: [(v) => !!v || "First name is required"],
    passwordRules: [(v) => !!v || "Password is required"],
    dateofbirthRules: [(v) => !!v || "Date of Birth is required"],
    lastnameRules: [(v) => !!v || "Last name is required"],
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
