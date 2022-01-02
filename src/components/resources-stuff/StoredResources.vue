<template>
  <ul>
    <resource-show
      v-for="data in resources"
      :key="data.id"
      :id="data.id"
      :title="data.title"
      :description="data.description"
      :link="data.link"
    ></resource-show>
  </ul>
</template>

<script>
import ResourceShow from './ResourceShow.vue';

export default {
  components: {
    ResourceShow,
  },
  inject: ['resources'],
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
