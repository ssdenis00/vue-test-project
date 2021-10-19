<template>
  <li class="item" v-bind:class="{ item_active: joke.isLiked }">
    <p class="joke">{{ joke.joke }}</p>
    <button
      type="button"
      aria-lable="like"
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
      if (this.joke.isLiked) {
        this.joke.isLiked = false;
        this.$emit("removeLike", this.joke);
      } else {
        this.joke.isLiked = true;
        this.$emit("getLike", this.joke);
      }
    },
  },
};
</script>

<style scoped>
@import url("./jokesItem.css");
</style>
