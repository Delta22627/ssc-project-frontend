<template>
  <v-row>
    <v-col
        v-for="n in 9"
        :key="n"
        class="d-flex child-flex"
        cols="4"
    >
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
    </v-col>
  </v-row>
</template>
<!--<template>-->
<!--  <v-container>-->
<!--    <div class="about">-->
<!--      <h1>This is an about page ttt</h1>-->
<!--    </div>-->
<!--  </v-container>-->
<!--  Add User rating-->
<!--  <v-rating-->
<!--    color="warning"-->
<!--    empty-icon="$mdiStarOutline"-->
<!--    full-icon="$mdiStar"-->
<!--    half-icon="$mdiStarHalfFull"-->
<!--    half-increments-->
<!--    hover-->
<!--    length="5"-->
<!--    size="64"-->
<!--    value="3"-->
<!--  ></v-rating>-->

<!--  Read only average rating-->
<!--  <v-rating-->
<!--    v-model="averageRating"-->
<!--    color="warning"-->
<!--    empty-icon="$mdiStarOutline"-->
<!--    full-icon="$mdiStar"-->
<!--    half-icon="$mdiStarHalfFull"-->
<!--    half-increments-->
<!--    hover-->
<!--    length="5"-->
<!--    readonly-->
<!--    size="64"-->
<!--    value="3"-->
<!--  ></v-rating>-->
<!--</template>-->

<!--<script>-->
<!--export default {-->
<!--  name: "Restaurant",-->
<!--  data: () => ({-->
<!--    averageRating: 4,-->
<!--  }),-->
<!--};-->
<!--</script>-->

<!--<style scoped></style>-->
