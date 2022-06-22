<template>
  <v-container class="container">
   <app-bar />
    <section class="pa-10">
      <v-row>
        <v-col cols="6"> </v-col>
        <v-col cols="6" class="d-flex justify-end">
          <section>
          <h1 style="font-size: 4rem">NFT</h1>
          <h1 style="font-size: 4rem">MARKETPLACE</h1>
          </section>
        </v-col>
      </v-row>
      <v-row class="mt-16 pt-5">
       <v-col cols="4">
          <v-card
            elevation="1"
            style="height: 15rem"
            :style="{
              'background-image':
                'url(' + require('../assets//nft.jpg') + ')',
                'background-position': 'center',
                'background-repeat': 'no-repeat',
                'background-size': 'cover'
            }"
          >
          </v-card>
        </v-col>
        <v-col cols="4">
           <v-card
            elevation="1"
            style="height: 15rem"
            :style="{
              'background-image':
                'url(' + require('../assets//eth.jpg') + ')',
                'background-position': 'center',
                'background-repeat': 'no-repeat',
                'background-size': 'cover'
            }"
          >
          </v-card>
        </v-col>
        <v-col cols="4">
           <v-card
            elevation="1"
            style="height: 15rem"
            :style="{
              'background-image':
                'url(' + require('../assets//crypto.jpg') + ')',
                'background-position': 'center',
                'background-repeat': 'no-repeat',
                'background-size': 'cover'
            }"
          >
          </v-card>
        </v-col>
      </v-row>
    </section>
  </v-container>
</template>

<script>
import AppBar from './AppBar.vue'
export default {
  name: "HomeComponent",
  components: {
    'app-bar': AppBar
  },

  data: () => ({}),
  computed: {
    timer() {
      var countDownDate = new Date("May 30, 2022 19:37:25").getTime();
      var now = new Date().getTime();

      // Find the distance between now and the count down date
      var distance = countDownDate - now;

      // Time calculations for days, hours, minutes and seconds
      var days = Math.floor(distance / (1000 * 60 * 60 * 24));
      var hours = Math.floor(
        (distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)
      );
      var minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
      var seconds = Math.floor((distance % (1000 * 60)) / 1000);

      return { days, hours, minutes, seconds };
    }
  }
};
</script>

<style scoped>
.title {
  font-size: 3rem !important;
}
</style>
