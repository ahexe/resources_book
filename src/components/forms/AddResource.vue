<template>
  <base-card>
    <form @submit.prevent="addResource">
      <div class="form-control">
        <label for="title">Title</label>
        <input v-model="enteredTitle" id="title" name="title" type="text" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea name="description" id="description" rows="3"></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input v-model="enteredLink" id="link" name="link" type="url" />
      </div>
      <div>
        <base-button type="submit">Add Resource</base-button>
      </div>
    </form>
  </base-card>
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
