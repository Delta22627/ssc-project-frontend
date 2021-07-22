<template>
  <v-container>
    <div class="createRes">
      <h1>Create a new Restaurant</h1>
    </div>
    <template>
      <v-form ref="form" v-model="valid" lazy-validation>
        <v-text-field
          v-model="restaurantName"
          :rules="restaurantNameRules"
          label="Restaurant Name"
          required
        ></v-text-field>

        <v-text-field
          v-model="description"
          :rules="aboutRules"
          label="About"
          required
        ></v-text-field>

        <v-text-field
          v-model="address"
          :rules="addressRules"
          label="Address"
          required
        ></v-text-field>

        <input
          type="file"
          @change="onFileSelected"
          class="form-control"
          ref="inputFile"
        />

        <div id="app"><img width="30%" :src="image" /> <HelloWorld /></div>

        <v-btn @click="onUpload" color="grey" class="mr-4"
          ><v-icon left>mdi-upload</v-icon>Upload</v-btn
        >

        <v-btn :disabled="!valid" color="primary" class="mr-4" @click="submit">
          <v-icon left>mdi-plus-circle</v-icon>Create
        </v-btn>
        <v-btn color="error" class="mr-4" @click="reset">
          <v-icon left>mdi-close-circle</v-icon>Reset</v-btn
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
    restaurantName: "",
    description: "",
    address: "",
    selectedFile: null,
    restaurantNameRules: [(v) => !!v || "Restaurant name is required"],
    aboutRules: [(v) => !!v || "Describe your restaurant"],
    addressRules: [(v) => !!v || "Address must be provided"],
    image: "",
  }),

  methods: {
    async submit() {
      if (this.$refs.form.validate()) {
        //submit to backend to authenticate

        let response = await Vue.axios.post("/api/restaurant", {
          name: this.restaurantName,
          description: this.description,
          address: this.address,
          photo: this.selectedFile,
        });

        if (response.data.success) {
          this.$router.push({ path: "/" });
        }
      }
    },

    reset() {
      window.location.reload();
    },

    onFileSelected(event) {
      var files = event.target.files;
      if (!files.length) return;
      this.createImage(files[0]);
      this.selectedFile = event.target.file[0];
    },
    onUpload() {},

    createImage(files) {
      var reader = new FileReader();
      reader.onload = (event) => {
        this.image = event.target.result;
      };
      reader.readAsDataURL(files);
    },
  },
};
</script>
