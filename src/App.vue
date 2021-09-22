<template>
  <div id="app">
    <img src="https://fontmeme.com/images/Pokemon-Logo.jpg" alt="logo">
    <h1>{{ message }}</h1>    
    <hooks />
  </div>
</template>

<script>
import hooks from "./components/hooks.vue";

export default {
  name: 'App',
  components: {
    hooks,
  },
  data() {
    return {
      message: "PokeGuía",
    }
  },
};
</script>

<style scoped>
#app {
  text-align: center;
  color: black;
  background: white;
}
img {
  width: 50vh;
  margin: -100px 0 -150px 0;

}
</style>