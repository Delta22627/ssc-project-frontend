<template>
  <v-container>
    <template>
      <v-form ref="form" v-model="valid" lazy-validation>
        <v-text-field
          v-model="username"
          :rules="usernameRules"
          label="Username"
          required
        ></v-text-field>

        <v-text-field
          v-model="firstname"
          :rules="firstNameRules"
          label="Firstname"
          required
        ></v-text-field>

        <v-text-field
          v-model="lastname"
          :rules="lastNameRules"
          label="Lastname"
          required
        ></v-text-field>

        <v-text-field
          v-model="dateofbirth"
          :rules="dateOfBirthRules"
          label="Date of Birth"
          required
        ></v-text-field>

        <v-text-field
          type="password"
          v-model="password"
          :rules="passwordRules"
          label="Password"
          required
        ></v-text-field>
        <div>
        <v-btn :disabled="!valid" color="success" class="mr-4" @click="submit">
          <v-icon left>
            mdi-account-plus
          </v-icon>
          Create
        </v-btn>
        </div>
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
    firstname: "",
    lastname: "",
    password: "",
    dateofbirth: "",
    usernameRules: [(v) => !!v || "User is required"],
    passwordRules: [(v) => !!v || "Password is required"],
    firstNameRules: [(v) => !!v || "First name is required"],
    lastNameRules: [(v) => !!v || "Last name is required"],
    dateOfBirthRules: [(v) => !!v || "Date of Birth is required"],

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
