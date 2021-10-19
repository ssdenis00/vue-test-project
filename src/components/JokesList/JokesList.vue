<template>
  <ul class="items">
    <JokesItem
      v-for="joke of jokes"
      :key="joke.id"
      v-bind:joke="joke"
      @getLike="getLike"
      @removeLike="removeLike"
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
    getLike(res) {
      this.$emit("getLike", res);
    },
    removeLike(res) {
      this.$emit("removeLike", res);
    },
  },
};
</script>
<style scoped>
@import url("./jokesList.css");
</style>
