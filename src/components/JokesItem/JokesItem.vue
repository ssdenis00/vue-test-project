<template>
  <li class="item" v-bind:class="{ item_active: joke.isLiked }">
    <p class="joke">{{ joke.joke }}</p>
    <button
      type="button"
      arial-lable="like"
      class="like"
      v-bind:class="{ like_active: joke.isLiked }"
      v-on:click="handleLikeClick"
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
  methods: {
    handleLikeClick() {
      this.joke.isLiked = !this.joke.isLiked;
      this.$emit("handleLikeClick", this.joke);
    },
  },
};
</script>

<style scoped>
@import url("./jokesItem.css");
</style>