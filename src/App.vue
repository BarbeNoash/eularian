<script lang="ts">
import JsonObserver from "./components/JsonObserver.vue";
import objectData from "../object-observer.json";

export default {
  components: {
    JsonObserver,
  },
  data() {
    return {
      data: objectData,
      showLocation: false,
      showAdress: false,
    };
  },
  methods: {
    showHide(eventType: string, elt: boolean) {
      if (eventType === "showLocation") {
        return (this.showLocation = !elt);
      }
      if (eventType === "showAdress") {
        return (this.showAdress = !elt);
      }
    },
  },
};
</script>

<template>
  <div class="wrapper">
    <JsonObserver :data="data" :showLocation="showLocation" :showAdress="showAdress" :showHide="showHide" />
  </div>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
