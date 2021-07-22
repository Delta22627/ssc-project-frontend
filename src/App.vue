<template>
  <v-app id="inspire">
    <div v-if="$route.name != 'Login'">
      <v-navigation-drawer v-model="drawer" app class="orange">
        <v-list-item>
          <v-list-item-content>
            <v-img
              src="https://images-ext-2.discordapp.net/external/oqct4MaV6IKrI6SjBuXuZq1tl4qeiO4A45GgCeUnxbQ/%3Fcompress%3D1%26resize%3D400x300/https/cdn.dribbble.com/users/95644/screenshots/8931405/media/3890e6f601cdf328377154c93a3b90de.png"
              alt=""
              contain
              height="100px"
              width="100px"
            >
            </v-img>
          </v-list-item-content>
        </v-list-item>

        <v-list dense nav>
          <v-list-item
            v-for="item in items"
            :key="item.title"
            :to="item.to"
            active-class="black--text"
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

      <v-app-bar
        app
        height="100px"
        src="https://image.shutterstock.com/image-photo/healthy-clean-food-cooking-eating-260nw-1847997298.jpg"
      >
        <v-app-bar-nav-icon
          color="orange"
          @click="drawer = !drawer"
        ></v-app-bar-nav-icon>

        <v-toolbar-title class="white--text">
          MUIC Restaurant Reviewer
        </v-toolbar-title>
        <v-spacer> </v-spacer>

        <v-form ref="form" v-model="valid" lazy-validation>
          <v-btn
            :disabled="!valid"
            color="dark yellow"
            class="mr-4"
            @click="submit"
            elevation="2"
            small
            ><v-icon left> mdi-logout</v-icon>Logout</v-btn
          >
        </v-form>
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
      { title: "Create New User", icon: "mdi-account-plus", to: "/createUser" },
      { title: "Create Restaurant", icon: "mdi-plus", to: "/createRestaurant" },
      { title: "Edit User", icon: "mdi-pencil", to: "/editUser" },
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
<style>
.box {
  background-color: #ffe57f;
  border-radius: 20px;
  padding: 10px;
  position: absolute;
  top: 60%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>
