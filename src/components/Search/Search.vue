<template>
  <form @submit.prevent="getValue" class="form">
    <input
      class="form__input"
      type="text"
      placeholder="Введите слово для поиска
    среди анекдотов..."
      v-model="inputResult"
      @keyup="getValue"
    />
  </form>
</template>

<script>
export default {
  data() {
    return {
      inputResult: "",
    };
  },
  methods: {
    getValue() {
      this.$emit("value", this.inputResult);
    },
  },
};
</script>
<style scoped>
@import url("./search.css");
</style>