<template>
  <div id="app">
    <Anime />
  </div>
</template>

<script>
import Anime from "./components/Anime.vue";
export default {
  name: "App",
  components: {
    Anime,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: top;
}
body {
  background-color:rgb(50, 50, 50);
  background-size: cover;
}
</style>