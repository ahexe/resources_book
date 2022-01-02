<template>
  <ul>
    <resource-show
      v-for="data in resources"
      :key="data.id"
      :id="data.id"
      :title="data.title"
      :description="data.description"
      :link="data.link"
      @delete-res="deleteResource(data.id)"
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
  methods: {
    deleteResource(dataId) {
      this.resources = this.resources.filter((data) => data.id !== dataId);
    },
  },
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
