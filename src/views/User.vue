<template>
  <v-container>

    <v-row justify="end">
      <v-col cols="12" sm="6" class="text-right">
        <v-btn :disabled="!valid" color="primary" class="mr-4" @click="edit"><v-icon left>mdi-pencil</v-icon>edit</v-btn>
        <v-btn :disabled="!valid" color="warning" class="mr-4" @click="add"><v-icon left>mdi-store</v-icon>Add your Restaurant</v-btn>
      </v-col>
    </v-row>

    <div class="user">
      <h1 class="my-3">User Information</h1>
    </div>
    <p >
      Name LastName
    </p>
    <p>
      Username
    </p>
    <p>
      DOB
    </p>
  </v-container>

</template>
<script>
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
    }
  }
};
</script>

