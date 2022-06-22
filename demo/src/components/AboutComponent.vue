<template>
  <v-container>
   <app-bar />
    <section class="pa-10 mt-15 d-flex align-center">
      <v-row>
        <v-col cols="6" class="d-flex align-center justify-center">
          <section>
            <h1 class="title">Our NFT Collection</h1>
            <p class="mt-5 description">
              Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
              eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut
              enim ad minim veniam, quis nostrud exercitation ullamco laboris
              nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in
              reprehenderit in voluptate velit esse cillum dolore eu fugiat
              nulla pariatur. Excepteur sint occaecat cupidatat non proident,
              sunt in culpa qui officia deserunt mollit anim id est laborum.
            </p>
          </section>
        </v-col>
        <v-col cols="6" class="d-flex align-center justify-center">
          <img src="../assets/NFT.jpeg" alt="" height="350" />
        </v-col>
      </v-row>
    </section>
  </v-container>
</template>

<script>
import AppBar from './AppBar.vue'
export default {
  name: "AboutComponent",
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
.description {
  font-size: 1.2rem !important;
}

.title {
  font-size: 3rem !important;
}
</style>
