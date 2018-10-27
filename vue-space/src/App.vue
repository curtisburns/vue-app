<template>

  <div id="app">
    <Nav />
    <LandingHero />
    <Articles />
  </div>

</template>

<script>
import Nav from './components/Nav.vue';
import LandingHero from './components/Landing-Hero.vue';
import Articles from './components/Articles.vue';

export default {
  name: 'app',
  components: {
    LandingHero,
    Nav,
    Articles
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

h1, h2, h3, h4 {
  margin-block-start: 0em;
  margin-block-end: 0em;
}

.content-wrapper {
  width: 900px;
}

.center-div {
  margin:auto;
}

</style>
