<template>
  <v-app id="inspire">
    <div v-if="$route.name != 'Login'">
      <v-navigation-drawer v-model="drawer" app>
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title class="text-h6">
              Restaurant Reviewer
            </v-list-item-title>
            <v-list-item-subtitle>
              Menu
              <v-form ref="form" v-model="valid" lazy-validation>
                <v-btn
                  :disabled="!valid"
                  color="success"
                  class="mr-4"
                  @click="submit"
                  >Logout</v-btn
                >
              </v-form>
            </v-list-item-subtitle>
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
      </v-navigation-drawer>

      <v-app-bar app>
        <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

        <v-toolbar-title> MUIC Restaurant Reviewer </v-toolbar-title>
      </v-app-bar>
    </div>

    <v-main>
      <router-view> </router-view>
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
      { title: "User", icon: "mdi-account", to: "/user" },
      { title: "Home", icon: "mdi-home", to: "/" },
      { title: "About", icon: "mdi-information", to: "/about" },
      { title: "Create", icon: "mdi-information", to: "/createuser" },
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
