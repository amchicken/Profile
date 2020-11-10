<template>
  <Parrallax/>
</template>

<script>
import Parrallax from './components/Parrallax.vue'

export default {
  name: 'App',
  components: {
    Parrallax
  },
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@100;400&display=swap');
@font-face {
  font-family: "VALORANT-Regular";

  src: url("./assets/fonts/ValorantFont.woff") format("woff"), /* Modern Browsers */
    url("./assets/fonts/ValorantFont.woff2") format("woff2"); /* Modern Browsers */
  font-weight: normal;
  font-style: normal;
}


* {
  font-family: 'Roboto', sans-serif;
  font-weight: 100;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

a {
  text-decoration: none;
}

body {
  background: #0f1922;
}
</style>
