<template>
  <div class="home container-spacer">
    <MyNftsComponent />
  </div>
</template>

<script>
// @ is an alias to /src
import MyNftsComponent from "@/components/MyNftsComponent.vue";

export default {
  name: "MyNfts",
  components: {
    MyNftsComponent,
  },
};
</script>
