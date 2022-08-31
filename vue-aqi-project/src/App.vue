<script>
import Homepage from "./components/Homepage/Homepage.vue";

export default {
  components: {
    Homepage
  }
}
</script>

<template>
  <Homepage/>
</template>

<style lang="scss">
html, body  {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  height: 100vh;
}

#app {
  height: 100%;
}
</style>
