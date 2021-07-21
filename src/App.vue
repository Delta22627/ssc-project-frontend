<template>
  <v-app id="inspire">
    <div v-if="$route.name != 'Login'">
      <v-navigation-drawer v-model="drawer" app>
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title class="text-h6" style="color:darkblue">
              Restaurant Reviewer
            </v-list-item-title>
            <v-list-item-subtitle> <h3 class="my-2" style="color:indianred" >List</h3></v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>

        <v-list dense nav>
          <v-list-item
            v-for="item in items"
            :key="item.title"
            :to="item.to"
            link
          >
            <v-list-item-icon>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title>{{ item.title }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
        <p></p>

        <template>
          <v-form ref="form" v-model="valid" lazy-validation align="center">
            <v-btn
              :disabled="!valid"
              color="warning"
              class="mr-4"
              @click="submit"
            >
              <v-icon left> mdi-exit-to-app</v-icon>
              Logout
            </v-btn>
          </v-form>
        </template>
      </v-navigation-drawer>
      <v-app-bar app>
        <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

        <v-toolbar-title> MUIC Restaurant Reviewer</v-toolbar-title>
      </v-app-bar>
    </div>

    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>
import Vue from "vue";

export default {
  name: "App",

  data: () => ({
    drawer: null,
    items: [
      { title: "User", icon: "mdi mdi-account", to: "/user" },
      { title: "Home", icon: "mdi-home", to: "/" },
      { title: "About", icon: "mdi-information", to: "/about" },
      { title: "Create", icon: "mdi-account-plus", to: "/createuser" },
    ],
    right: null,
  }),

  methods: {
    async submit() {
      if (this.$refs.form.validate()) {
        //submit to backend to authenticate
        let response = await Vue.axios.get("/api/logout");
        if (response.data.success) {
          this.$router.push({ path: "/login" });
        }
      }
    },
    reset() {
      this.$refs.form.reset();
    },
  },
};
</script>
