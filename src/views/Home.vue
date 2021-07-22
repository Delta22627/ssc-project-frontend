
<template>

  <v-container>
<!--    <h2>Home Page</h2>-->
<!--    <ul>-->
<!--      <li>-->
<!--        <router-link to="/">Go to Home</router-link>-->
<!--      </li>-->
<!--      <li>-->
<!--        <router-link to="/about">Go to About</router-link>-->
<!--      </li>-->
<!--      <li>-->
<!--        <router-link to="/login">Go to Login</router-link>-->
<!--      </li>-->
<!--    </ul>-->
    <v-row>
      <v-col
          v-for="n in 10"
          :key="n"
          class="d-flex child-flex"
          cols="6"
      >
        <v-card>
        <v-img
            :src="`https://picsum.photos/500/300?image=${n * 5 + 10}`"
            :lazy-src="`https://picsum.photos/10/6?image=${n * 5 + 10}`"
            aspect-ratio="1"
            class="grey lighten-2"
        >
          <template v-slot:placeholder>
            <v-row
                class="fill-height ma-0"
                align="center"
                justify="center"
            >
              <v-progress-circular
                  indeterminate
                  color="grey lighten-5"
              ></v-progress-circular>
            </v-row>
          </template>
        </v-img>

          <h1>Name</h1>
          <h2>Info</h2>
        <v-rating>
          v-model ="averageRating"
          color ="amber"
          empty-icon="$mdiStarOutline"
          full-icon="$mdiStar"
          half-icon="$mdiStarHalfFull"
          half-increments
          hover
          length="5"
          readonly
          size="64"
          value="3"
          ></v-rating>
        </v-card>
      </v-col>
    </v-row>
  </v-container>


</template>

<script>
export default {
  name: 'Home',
  data: () => ({
    averageRating: 4,
  }),
  components: {

  },
}
</script>
