<template>
  <ul>
    <Learning-ressource
      v-for="item in storedResources"
      :title="item.title"
      :link="item.link"
      :description="item.description"
      :key="item.id"
    />
  </ul>
</template>
<script>
import LearningRessource from './LearningRessource.vue';

export default {
  inject: ['storedResources'],
  components: { LearningRessource },

};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>
