<template>
  <v-container>
    <div class="EditUser">
      <h1>Edit User's Password</h1>
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

        <v-row justify="space-around">
          <v-col>
            <v-dialog
                transition="dialog-bottom-transition"
                max-width="600"
            >
              <template v-slot:activator="{ on, attrs }">
                <v-btn
                    color="primary"
                    v-bind="attrs"
                    v-on="on"
                    :disabled="!valid" class="mr-4" @click="submit"
                ><v-icon left>mdi-check</v-icon>CONFIRM</v-btn>
              </template>
              <template v-slot:default="dialog">
                <v-card>
                  <v-toolbar
                      color="green"
                      dark
                  >Successfully!</v-toolbar>
                  <v-card-text>
                    <div class="text-h2 pa-12">Changed Password Successfully
                    </div>
                  </v-card-text>
                  <v-card-actions class="justify-end">
                    <v-btn
                        text
                        @click="dialog.value = false"
                    >Close</v-btn>
                  </v-card-actions>
                </v-card>
              </template>
            </v-dialog>
            <v-btn :disabled="!valid" color="error" class="mr-4" @click="reset"
            ><v-icon left>mdi-close-circle</v-icon>reset</v-btn>
          </v-col>
        </v-row>
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

        let response = await Vue.axios.post("/api/user/password", {
          username: this.username,
          password: this.password,
          newPassword: this.newPassword,
        });

        if (response.data.success) {
          this.$router.push({ path: "/" });
        }
      }
    },
    reset() {
      this.$refs.form.reset();
    },
  }
}
</script>
