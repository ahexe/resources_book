<template>
  <form @submit.prevent="addResource">
    <base-card>
      <div class="form-control">
        <label>Title</label>
        <input v-model="enteredTitle" type="text" />
      </div>
      <div class="form-control">
        <label>Description</label>
        <input v-model="enteredDescription" type="text" />
      </div>
      <div class="form-control">
        <label>Link</label>
        <input v-model="enteredLink" type="url" />
      </div>
      <base-button>Add Resource</base-button>
    </base-card>
  </form>
</template>

<script>
export default {
  emits: ['add-res'],
  data() {
    return {
      enteredTitle: '',
      enteredDescription: '',
      enteredLink: '',
    };
  },
  methods: {
    addResource() {
      if (this.enteredTitle) {
        this.$emit(
          'add-res',
          this.enteredTitle,
          this.enteredDescription,
          this.enteredLink
        );
        this.enteredTitle = '';
        this.enteredDescription = '';
        this.enteredLink = '';
      }
      // todo  else
    },
  },
};
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>
