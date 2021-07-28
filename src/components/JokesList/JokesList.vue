<template>
  <ul class="items">
    <JokesItem />
  </ul>
</template>

<script>
import JokesItem from "@/components/JokesItem/JokesItem";
export default {
  components: {
    JokesItem,
  },
};
</script>
<style scoped>
@import url("./jokesList.css");
</style>
