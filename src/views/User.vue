<template>
  <v-container>
    <v-row justify="end">
      <v-col cols="12" sm="6" class="text-right">
        <v-btn :disabled="!valid" color="primary" class="mr-4" @click="edit"
          ><v-icon left>mdi-pencil</v-icon>edit</v-btn
        >
        <v-btn :disabled="!valid" color="warning" class="mr-4" @click="add"
          ><v-icon left>mdi-store</v-icon>Add your Restaurant</v-btn
        >
      </v-col>
    </v-row>

    <div class="user">
      <h1 class="my-3">
        Top Secret <v-icon color="red">mdi-alarm-light</v-icon
        ><v-icon color="blue">mdi-alarm-light</v-icon>
      </h1>
    </div>
    <p>This is one of the top secret information from Area52</p>
    <p>
      Normal citizen without authority are not allowed to see or even know about
      this information
    </p>
    <p style="color: red">
      Logout or your device will be hacked!!
      <v-icon color="black">mdi-bomb mdi-spin </v-icon>
      <v-icon color="green">mdi-dna mdi-spin </v-icon>
      <v-icon color="warning">mdi-incognito mdi-spin </v-icon>
    </p>
    <v-btn
      :disabled="!valid"
      color="red"
      class="mr-4"
      @click="submit"
      elevation="2"
      big
      ><v-icon left> mdi-logout</v-icon>Logout NOW!!!</v-btn
    >
  </v-container>
</template>
<script>
import Vue from "vue";

export default {
  data: () => ({
    valid: true,
    firstname: "",
    lastname: "",
    dateofbirth: "",
  }),

  methods: {
    async edit() {
      this.$router.push({path: "/editUser"});
    },
    async add() {
      this.$router.push({path: "/createRestaurant"});
    },

    async submit() {
      if (this.$refs.form.validate()) {
        //submit to backend to authenticate
        let response = await Vue.axios.get("/api/logout");
        if (response.data.success) {
          this.$router.push({path: "/"});
        }
      }
    }, reset() {
      this.$refs.form.reset();
    },
  },
};
</script>
