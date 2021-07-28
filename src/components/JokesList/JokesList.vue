<template>
  <ul class="items">
    <JokesItem v-for="joke of jokes" :key="joke" v-bind:joke="joke" />
  </ul>
</template>

<script>
import JokesItem from "@/components/JokesItem/JokesItem";
export default {
  props: ["jokes"],
  components: {
    JokesItem,
  },
};
</script>
<style scoped>
@import url("./jokesList.css");
</style>
