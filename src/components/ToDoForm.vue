<template>
  <form @submit.prevent="onSubmit">
    <label for="new-todo-input" class="label__lg">
      What needs to be done?
    </label>
    <input
      type="text"
      id="new-todo-input"
      name="new-todo"
      autocomplete="off"
      v-model.trim.lazy="words"
      class="input__lg"
    />
    <button type="submit" class="btn btn__primary btn__lg">Add</button>
  </form>
</template>
<script>
export default {
  methods: {
    onSubmit() {
      if (this.words === "") {
        return;
      }
      this.$emit("todo-added", this.words);
      this.words = "";
    },
  },
  data() {
    return {
      words: "",
    };
  },
};
</script>