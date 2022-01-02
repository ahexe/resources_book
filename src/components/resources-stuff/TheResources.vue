<template>
  <base-card>
    <base-button
      @click="setSelectedTab('stored-resources')"
      :mode="storedResButtonMode"
      >Stored Resources</base-button
    >
    <base-button
      @click="setSelectedTab('add-resource')"
      :mode="addResButtonMode"
      >Add Resources</base-button
    >
  </base-card>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import StoredResources from './StoredResources.vue';
import AddResource from '../forms/AddResource.vue';

export default {
  components: {
    StoredResources,
    AddResource,
  },
  data() {
    return {
      selectedTab: 'stored-resources',
      storedData: [
        {
          id: '1',
          title: 'Google',
          description: 'a search engine',
          link: 'https://www.google.com',
        },
        {
          id: '2',
          title: 'W3School',
          description: 'An online school',
          link: 'https://www.w3schools.com/',
        },
        {
          id: '3',
          title: 'JS Book',
          description: 'a simple book',
          link: '',
        },
      ],
    };
  },
  provide() {
    return {
      resources: this.storedData,
      addResource: this.addToStoredData,
      removeResource: this.removeResource,
    };
  },
  computed: {
    storedResButtonMode() {
      return this.selectedTab === 'stored-resources' ? null : 'flat';
    },
    addResButtonMode() {
      return this.selectedTab === 'add-resource' ? null : 'flat';
    },
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addToStoredData(title, description, link) {
      const source = {
        id: new Date().toISOString(),
        title: title,
        description: description,
        link: link,
      };
      this.storedData.unshift(source);
      this.selectedTab = 'stored-resources';
    },
    removeResource(resID) {
      const resIndex = this.storedData.findIndex((data) => data.id === resID);
      this.storedData.splice(resIndex, 1);
    },
  },
};
</script>
