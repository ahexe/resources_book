<template>
  <li>
    <base-card>
      <header>
        <h3>{{ title }}</h3>
        <base-button mode="flat" @click="removeResource(id)"
          >Delete</base-button
        >
      </header>
      <p>{{ checkDescriptionExist }}</p>
      <nav>
        <a :href="checkLinkExist">View Resource</a>
      </nav>
    </base-card>
  </li>
</template>

<script>
export default {
  inject: ['removeResource'],
  props: {
    id: {
      type: String,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
    description: {
      type: String,
      required: false,
    },
    link: {
      type: String,
      required: false,
    },
  },
  computed: {
    checkDescriptionExist() {
      return this.description
        ? this.description
        : 'Search in Google for more information';
    },
    checkLinkExist() {
      return this.link
        ? this.link
        : 'https://www.google.com/search?q=' + this.title;
    },
  },
};
</script>

<style scoped>
li {
  margin: auto;
  max-width: 40rem;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h3 {
  font-size: 1.25rem;
  margin: 0.5rem 0;
}

p {
  margin: 0.5rem 0;
}

a {
  text-decoration: none;
  color: #ce5c00;
}

a:hover,
a:active {
  color: #c89300;
}
</style>
