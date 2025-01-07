<template>
  <base-dialog title="validation impossible" v-if="inputIsInvalid">
    <template #default>
      <p>un champ est invalide</p>
    </template>
    <template #actions>
      <base-button @click="confirmError">Ok</base-button>
    </template>
  </base-dialog>
  <base-card>
    <form @submit.prevent="sendForm">
      <div class="form-control">
        <label for="title">title</label>
        <input ref="title" type="text" name="title" id="title" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          ref="description"
          type="text"
          name="description"
          rows="3"
          id="description"
        ></textarea>
      </div>
      <div class="form-control">
        <label for="url">Link</label>
        <input ref="link" type="url" name="link" id="link" />
      </div>
      <div>
        <base-button type="submit">envoyer</base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
export default {
  inject: ['AddRessource'],
  data() {
    return {
      inputIsInvalid: false,
    };
  },
  methods: {
    sendForm() {
      const title = this.$refs.title.value;
      const description = this.$refs.description.value;
      const link = this.$refs.link.value;

      if (
        title.trim() === '' ||
        description.trim() === '' ||
        link.trim() === ''
      ) {
        this.inputIsInvalid = true;
        return;
      }
      this.AddRessource(title, description, link);
    },

    confirmError() {
      this.inputIsInvalid = false;
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
