<template>
  <the-header title="rappelle moi" />
  <the-ressource />
</template>

<script>
import TheHeader from './components/layouts/TheHeader.vue';
import TheRessource from './components/resources/TheRessource.vue';
export default {
  components: {
    TheHeader,
    TheRessource,
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>
