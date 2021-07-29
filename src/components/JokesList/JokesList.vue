<template>
  <ul class="items">
    <JokesItem
      v-for="joke of jokes"
      :key="joke.id"
      v-bind:joke="joke"
      @handleLikeClick="handleLikeClick"
    />
  </ul>
</template>

<script>
import JokesItem from "@/components/JokesItem/JokesItem";
export default {
  props: ["jokes"],
  components: {
    JokesItem,
  },
  methods: {
    handleLikeClick(res) {
      this.$emit("handleLikeClick", res);
    },
  },
};
</script>
<style scoped>
@import url("./jokesList.css");
</style>
