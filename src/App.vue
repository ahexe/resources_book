<template>
  <the-header title="Learning Resources"></the-header>
  <stored-resources :stored-data="this.storedData"></stored-resources>
</template>

<script>
import StoredResources from './components/resources-stuff/StoredResources.vue';
import TheHeader from './components/layouts/TheHeader.vue';

export default {
  components: {
    StoredResources,
    TheHeader,
  },
  data() {
    return {
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
