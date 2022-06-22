<template>
  <div class="home container-spacer">
    <FaqsComponent />
  </div>
</template>

<script>
// @ is an alias to /src
import FaqsComponent from "@/components/FaqsComponent.vue";

export default {
  name: "FAQs",
  components: {
    FaqsComponent,
  },
};
</script>
