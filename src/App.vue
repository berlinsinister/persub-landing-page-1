<template>
  <LandingPage />
</template>

<script>
import LandingPage from "./components/LandingPage.vue";

export default {
  name: "App",
  components: { LandingPage },
  data() {
    return {};
  },
};
</script>

<style lang="scss">
@import "./assets/sass/vars";
@import "./assets/sass/mixins";

:root {
  font-size: $font-size;
}

html,
body {
  @include reset;
}

body {
  font: {
    family: $font-family;
    size: 1.4rem;
    weight: 400;
  }
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background: black;
}
</style>
