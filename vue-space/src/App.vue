<template>

  <div id="app">
    <Nav />
    <LandingHero />
  </div>

</template>

<script>
import LandingHero from './components/Landing-Hero.vue';
import Nav from './components/Nav.vue';

export default {
  name: 'app',
  components: {
    LandingHero,
    Nav
  }
}
</script>

<style>
body {
  margin: 0;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

h1 {
  margin-block-start: 0em;
  margin-block-end: 0em;
}
</style>
