<template>
  <v-container class="container">
    <app-bar />
    <section class="pa-10 mt-15">
      <v-expansion-panels>
        <v-expansion-panel style="background: #033856; color: #fff;" class="mb-3">
          <v-expansion-panel-header>
            <h1>What is a Non-Fungible Token?</h1>
          </v-expansion-panel-header>
          <v-expansion-panel-content>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla vitae
            quam vitae est fermentum imperdiet ultricies vel mi. Donec maximus
            metus ac mattis sollicitudin. Fusce placerat nec dolor in tempor.
            Nullam rutrum sit amet est facilisis sagittis. Proin ut sem sit amet
            mi vehicula pellentesque at ut odio. Proin auctor tortor ac tellus
            ultrices, porttitor ultrices elit fermentum. Proin maximus nulla
            faucibus, tristique quam sit amet, hendrerit nulla. Cras vehicula
            viverra ipsum, a tempor felis sagittis ac. Etiam laoreet nec quam
            vel facilisis. Curabitur enim lorem, imperdiet a erat nec, rhoncus
            convallis purus. Nulla facilisi.
          </v-expansion-panel-content>
        </v-expansion-panel>

        <v-expansion-panel style="background: #033856; color: #fff;" class="mb-3">
          <v-expansion-panel-header>
            <h1>Where can I buy a Non-Fungible Token?</h1>
          </v-expansion-panel-header>
          <v-expansion-panel-content>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla vitae
            quam vitae est fermentum imperdiet ultricies vel mi. Donec maximus
            metus ac mattis sollicitudin. Fusce placerat nec dolor in tempor.
            Nullam rutrum sit amet est facilisis sagittis. Proin ut sem sit amet
            mi vehicula pellentesque at ut odio. Proin auctor tortor ac tellus
            ultrices, porttitor ultrices elit fermentum. Proin maximus nulla
            faucibus, tristique quam sit amet, hendrerit nulla. Cras vehicula
            viverra ipsum, a tempor felis sagittis ac. Etiam laoreet nec quam
            vel facilisis. Curabitur enim lorem, imperdiet a erat nec, rhoncus
            convallis purus. Nulla facilisi.
          </v-expansion-panel-content>
        </v-expansion-panel>

        <v-expansion-panel style="background: #033856; color: #fff;" class="mb-3">
          <v-expansion-panel-header>
            <h1>What is a wallet?</h1>
          </v-expansion-panel-header>
          <v-expansion-panel-content>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla vitae
            quam vitae est fermentum imperdiet ultricies vel mi. Donec maximus
            metus ac mattis sollicitudin. Fusce placerat nec dolor in tempor.
            Nullam rutrum sit amet est facilisis sagittis. Proin ut sem sit amet
            mi vehicula pellentesque at ut odio. Proin auctor tortor ac tellus
            ultrices, porttitor ultrices elit fermentum. Proin maximus nulla
            faucibus, tristique quam sit amet, hendrerit nulla. Cras vehicula
            viverra ipsum, a tempor felis sagittis ac. Etiam laoreet nec quam
            vel facilisis. Curabitur enim lorem, imperdiet a erat nec, rhoncus
            convallis purus. Nulla facilisi.
          </v-expansion-panel-content>
        </v-expansion-panel>
        <v-expansion-panel style="background: #033856; color: #fff;" class="mb-3">
          <v-expansion-panel-header>
            <h1>How can I create a wallet?</h1>
          </v-expansion-panel-header>
          <v-expansion-panel-content>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla vitae
            quam vitae est fermentum imperdiet ultricies vel mi. Donec maximus
            metus ac mattis sollicitudin. Fusce placerat nec dolor in tempor.
            Nullam rutrum sit amet est facilisis sagittis. Proin ut sem sit amet
            mi vehicula pellentesque at ut odio. Proin auctor tortor ac tellus
            ultrices, porttitor ultrices elit fermentum. Proin maximus nulla
            faucibus, tristique quam sit amet, hendrerit nulla. Cras vehicula
            viverra ipsum, a tempor felis sagittis ac. Etiam laoreet nec quam
            vel facilisis. Curabitur enim lorem, imperdiet a erat nec, rhoncus
            convallis purus. Nulla facilisi.
          </v-expansion-panel-content>
        </v-expansion-panel>
      </v-expansion-panels>
    </section>
  </v-container>
</template>

<script>
import AppBar from './AppBar.vue'
export default {
  name: "FaqsComponent",
   components: {
    'app-bar': AppBar
  },

  data: () => ({}),

};
</script>
<style scoped>
.v-expansion-panel::before {
  border-radius: inherit;
  bottom: 0;
  content: "";
  left: 0;
  position: absolute;
  right: 0;
  top: 0;
  z-index: -1;
  transition: box-shadow 280ms cubic-bezier(0.4, 0, 0.2, 1);
  box-shadow: none !important;
}

.v-expansion-panels {
  border-radius: 15px !important;
}
</style>
