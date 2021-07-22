<template>
  <v-container>
    <div class="EditRestaurant">
      <h1> Edit Restaurant {Restaurant Name}</h1>
    </div>
    <template>
      <v-form ref="form" v-model="valid" lazy-validation>

        <v-text-field
            v-model="RestaurantName"
            :rules="RestaurantNameRule"
            label="Restaurant Name"
            required
        ></v-text-field>

        <v-text-field
            v-model="About"
            :rules="AboutRule"
            label="About"
            required
        ></v-text-field>

        <v-text-field
            v-model="Address"
            :rules="AddressRule"
            label="Address"
            required
        ></v-text-field>


        <input type="file" @change="onFileSelected" class="form-control" ref="inputFile"/>
        <div id="app"><img width="30%" :src="image" /> <HelloWorld /></div>
        <v-btn @click="onUpload" color="grey" class="mr-4"><v-icon>mdi-upload</v-icon>Upload</v-btn>


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
    RestaurantName: "",
    About: "",
    Address: "",
    selectedFile: null,
    image:"",
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
          this.$router.push({path: "/"});
        }
      }
    },
    reset() {
      window.location.reload();
    },
    onFileSelected(event) {
      var files = event.target.files
      if (!files.length)
        return
      this.createImage(files[0]);
      this.selectedFile = event.target.file[0]
    },
    onUpload() {
    },
    createImage(files){
      var reader = new FileReader();
      reader.onload = (event) => {
        this.image = event.target.result;
      }
      reader.readAsDataURL(files)
    },
  }
};
</script>
