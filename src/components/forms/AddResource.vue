<template>
  <base-dialog
    v-if="inputDialog"
    :title="enteredTitle ? enteredTitle : 'Invalid Input'"
    @close="confirmError"
  >
    <template #default>
      <p>Unfortunately the Title can't be empty.</p>
      <p>Please enter the Title.</p>
    </template>
    <template #actions>
      <base-button @click="confirmError">OK</base-button>
    </template>
  </base-dialog>
  <base-card>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title</label>
        <input v-model="enteredTitle" id="title" name="title" type="text" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          v-model="enteredDescription"
          name="description"
          id="description"
          rows="3"
        ></textarea>
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
import BaseButton from '../UI/BaseButton.vue';
export default {
  components: { BaseButton },
  inject: ['addResource'],
  data() {
    return {
      inputDialog: false,
      enteredTitle: '',
      enteredDescription: '',
      enteredLink: '',
    };
  },
  methods: {
    submitData() {
      if (this.enteredTitle.trim() !== '') {
        this.addResource(
          this.enteredTitle,
          this.enteredDescription,
          this.enteredLink
        );
        this.enteredTitle = '';
        this.enteredDescription = '';
        this.enteredLink = '';
      } else {
        this.inputDialog = true;
      }
    },
    confirmError() {
      this.inputDialog = false;
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
