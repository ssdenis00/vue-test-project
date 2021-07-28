<template>
  <li class="item" v-bind:class="{ item_active: joke.isLiked }">
    <p class="joke">{{ joke.title }}</p>
    <button
      type="button"
      arial-lable="like"
      class="like"
      v-bind:class="{ like_active: joke.isLiked }"
      v-on:click="joke.isLiked = !joke.isLiked"
    ></button>
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