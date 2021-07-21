<template>
  <v-container>
    <div class="about">
      <h1>This is an about page ttt</h1>
    </div>
  </v-container>
  Add User rating
  <v-rating
    color="warning"
    empty-icon="$mdiStarOutline"
    full-icon="$mdiStar"
    half-icon="$mdiStarHalfFull"
    half-increments
    hover
    length="5"
    size="64"
    value="3"
  ></v-rating>

  Read only average rating
  <v-rating
    v-model="averageRating"
    color="warning"
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
</template>

<script>
export default {
  name: "Restaurant",
  data: () => ({
    averageRating: 4,
  }),
};


</script>

<style scoped>

</style>