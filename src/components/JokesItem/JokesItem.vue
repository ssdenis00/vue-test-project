<template>
  <li class="item">
    <p class="joke">{{ joke.title }}</p>
    <button type="button" arial-lable="like" class="like"></button>
  </li>
</template>

<script>
export default {
  props: {
    joke: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped>
@import url("./jokesItem.css");
</style>