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
      <v-col v-for="n in 1" :key="n" class="d-flex child-flex">
        <v-card>
          <v-img
              src="https://img.wongnai.com/p/1920x0/2019/05/29/e81a8c134df04d43a47d28bebb4a925c.jpg"
            :lazy-src="`/photos/kfc.jpg${n * 5 + 10}`"
            aspect-ratio="1"
            class="grey lighten-2"
          >
            <template v-slot:placeholder>
              <v-row class="fill-height ma-0" align="center" justify="center">
                <v-progress-circular
                  indeterminate
                  color="grey lighten-5"
                ></v-progress-circular>
              </v-row>
            </template>
          </v-img>
          <h1>Greyhound Café @Emquatier</h1>
          <h2>Greyhound Café offer more than 20 new menus, presented through a unique style , making every menu full of delicious flavors. </h2>
          <v-rating>
            v-model ="averageRating" color ="amber" empty-icon="$mdiStarOutline"
            full-icon="$mdiStar" half-icon="$mdiStarHalfFull" half-increments
            hover length="5" readonly size="64" value="3" ></v-rating
          >
        </v-card>
      </v-col>
      <v-col v-for="n in 1" :key="n" class="d-flex child-flex">
        <v-card>
          <v-img
             src="https://img.wongnai.com/p/1920x0/2019/05/07/78c769ab97e245c18912e552601cd73f.jpg"
            lazy-src="`https://picsum.photos/10/6?image=`"
            aspect-ratio="1"
            class="grey lighten-2"
          >
            <template v-slot:placeholder>
              <v-row class="fill-height ma-0" align="center" justify="center">
                <v-progress-circular
                  indeterminate
                  color="grey lighten-5"
                ></v-progress-circular>
              </v-row>
            </template>
          </v-img>
          <h1>KFC @Central WestGate</h1>
          <h2>Best known for their fried chicken, with a 100 years recipe.</h2>
          <v-rating>
            v-model ="averageRating" color ="amber" empty-icon="$mdiStarOutline"
            full-icon="$mdiStar" half-icon="$mdiStarHalfFull" half-increments
            hover length="5" readonly size="64" value="3" ></v-rating
          >
        </v-card>
      </v-col>
      <v-col v-for="n in 1" :key="n" class="d-flex child-flex">
        <v-card>
          <v-img
              src="https://ed.edtfiles-media.com/static-cache/resize-cache/wk18/ud/gal/dcp/30/88494/LUM_0100.jpg"
            :lazy-src="`https://picsum.photos/10/6?image=${n * 5 + 10}`"
            aspect-ratio="1"
            class="grey lighten-2"
          >
            <template v-slot:placeholder>
              <v-row class="fill-height ma-0" align="center" justify="center">
                <v-progress-circular
                  indeterminate
                  color="grey lighten-5"
                ></v-progress-circular>
              </v-row>
            </template>
          </v-img>
          <h1>BonChon @Central World</h1>
          <h2>Best known for selling Korean food, pretty popular with their variety of chicken flavor.</h2>
          <v-rating>
            v-model ="averageRating" color ="amber" empty-icon="$mdiStarOutline"
            full-icon="$mdiStar" half-icon="$mdiStarHalfFull" half-increments
            hover length="5" readonly size="64" value="3" ></v-rating
          >
        </v-card>
      </v-col>
    </v-row>
    <v-row>
      <v-col v-for="n in 1" :key="n" class="d-flex child-flex">
        <v-card>
          <v-img
            src="https://img.wongnai.com/p/1920x0/2017/08/26/4d6d7a6592ae43f585d07fc349acf4cf.jpg"
            :lazy-src="`https://picsum.photos/10/6?image=${n * 5 + 10}`"
            aspect-ratio="1"
            class="grey lighten-2"
          >
            <template v-slot:placeholder>
              <v-row class="fill-height ma-0" align="center" justify="center">
                <v-progress-circular
                  indeterminate
                  color="grey lighten-5"
                ></v-progress-circular>
              </v-row>
            </template>
          </v-img>
          <h1>Texas Chicken @Central Bangna</h1>
          <h2>Their honey butter biscuit must be one of the best in Thailand, pretty sweet and soft, best to eat while it's hot.</h2>
          <v-rating>
            v-model ="averageRating" color ="amber" empty-icon="$mdiStarOutline"
            full-icon="$mdiStar" half-icon="$mdiStarHalfFull" half-increments
            hover length="5" readonly size="64" value="3" ></v-rating
          >
        </v-card>
      </v-col>
      <v-col v-for="n in 1" :key="n" class="d-flex child-flex">
        <v-card>
          <v-img
              src="https://www.checkraka.com/uploaded/article/preview/1039/place-03.jpg"
            :lazy-src="`https://picsum.photos/10/6?image=${n * 5 + 10}`"
            aspect-ratio="1"
            class="grey lighten-2"
          >
            <template v-slot:placeholder>
              <v-row class="fill-height ma-0" align="center" justify="center">
                <v-progress-circular
                  indeterminate
                  color="grey lighten-5"
                ></v-progress-circular>
              </v-row>
            </template>
          </v-img>
          <h1>Burger King @Little Walk</h1>
          <h2>Foods are pretty expensive, specially the one at airport. However, their "Double BBQ Bacon Cheese" is the best!!!</h2>
          <v-rating>
            v-model ="averageRating" color ="amber" empty-icon="$mdiStarOutline"
            full-icon="$mdiStar" half-icon="$mdiStarHalfFull" half-increments
            hover length="5" readonly size="64" value="3" ></v-rating
          >
        </v-card>
      </v-col>
      <v-col v-for="n in 1" :key="n" class="d-flex child-flex">
        <v-card>
          <v-img
              src="http://www.bestdesignguides.com/wp-content/uploads/2013/08/Top-5-most-expensive-restaurants-in-Moscow-1-Copy.jpg"
            :lazy-src="`https://picsum.photos/10/6?image=${n * 5 + 10}`"
            aspect-ratio="1"
            class="grey lighten-2"
          >
            <template v-slot:placeholder>
              <v-row class="fill-height ma-0" align="center" justify="center">
                <v-progress-circular
                  indeterminate
                  color="grey lighten-5"
                ></v-progress-circular>
              </v-row>
            </template>
          </v-img>
          <h1>LONG INW FOOD AROI @MOON</h1>
          <h2>Best restaurant EVER!!!, Chef are from German (RECOMMENDED)</h2>
          <v-rating>
            v-model ="averageRating" color ="amber" empty-icon="$mdiStarOutline"
            full-icon="$mdiStar" half-icon="$mdiStarHalfFull" half-increments
            hover length="5" readonly size="64" value="3" ></v-rating
          >
        </v-card>
      </v-col>
    </v-row>
    <v-row>
      <v-col v-for="n in 1" :key="n" class="d-flex child-flex">
        <v-card>
          <v-img
              src="https://img.thai2night.com/shop/photo_cover/master/20190527095324QDbFFeLMh7.jpg"
            :lazy-src="`https://picsum.photos/10/6?image=${n * 5 + 10}`"
            aspect-ratio="1"
            class="grey lighten-2"
          >
            <template v-slot:placeholder>
              <v-row class="fill-height ma-0" align="center" justify="center">
                <v-progress-circular
                  indeterminate
                  color="grey lighten-5"
                ></v-progress-circular>
              </v-row>
            </template>
          </v-img>
          <h1>About US @Salaya</h1>
          <h2>Always filled with under age person. Good music and girls.</h2>
          <v-rating>
            v-model ="averageRating" color ="amber" empty-icon="$mdiStarOutline"
            full-icon="$mdiStar" half-icon="$mdiStarHalfFull" half-increments
            hover length="5" readonly size="64" value="3" ></v-rating
          >
        </v-card>
      </v-col>
      <v-col v-for="n in 1" :key="n" class="d-flex child-flex">
        <v-card>
          <v-img
              src="https://d136usn7jnoe61.cloudfront.net/pictures/22400/s2n_0070_p1dl7a1el160112fs58uben1pu82b.jpg"
            :lazy-src="`https://picsum.photos/10/6?image=${n * 5 + 10}`"
            aspect-ratio="1"
            class="grey lighten-2"
          >
            <template v-slot:placeholder>
              <v-row class="fill-height ma-0" align="center" justify="center">
                <v-progress-circular
                  indeterminate
                  color="grey lighten-5"
                ></v-progress-circular>
              </v-row>
            </template>
          </v-img>
          <h1>Baby Face @Thonglor</h1>
          <h2>Lots of beautiful girl, always crowed, would recommended if you are single!</h2>
          <v-rating>
            v-model ="averageRating" color ="amber" empty-icon="$mdiStarOutline"
            full-icon="$mdiStar" half-icon="$mdiStarHalfFull" half-increments
            hover length="5" readonly size="64" value="3" ></v-rating
          >
        </v-card>
      </v-col>
      <v-col v-for="n in 1" :key="n" class="d-flex child-flex">
        <v-card>
          <v-img
              src="https://f.ptcdn.info/552/065/000/pwf9n314ump1mZqRMn-o.png"
            :lazy-src="`https://picsum.photos/10/6?image=${n * 5 + 10}`"
            aspect-ratio="1"
            class="grey lighten-2"
          >
            <template v-slot:placeholder>
              <v-row class="fill-height ma-0" align="center" justify="center">
                <v-progress-circular
                  indeterminate
                  color="grey lighten-5"
                ></v-progress-circular>
              </v-row>
            </template>
          </v-img>
          <h1>BEST BEEF @Sukhumvit 51</h1>
          <h2>Food ordering are very slow, long queue, hot, but! not expensive and have free ice-cream.</h2>
          <v-rating>
            v-model ="averageRating" color ="amber" empty-icon="$mdiStarOutline"
            full-icon="$mdiStar" half-icon="$mdiStarHalfFull" half-increments
            hover length="5" readonly size="64" value="3" ></v-rating
          >
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "Home",
  data: () => ({
    averageRating: 4,
  }),
  components: {},
};
</script>
