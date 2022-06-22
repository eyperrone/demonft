<template>
  <div class="home container-spacer">
    <CollectionsComponent />
  </div>
</template>

<script>
// @ is an alias to /src
import CollectionsComponent from "@/components/CollectionsComponent.vue";

export default {
  name: "Collections",
  components: {
    CollectionsComponent,
  },
};
</script>
