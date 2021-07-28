<template>
  <div id="app">
    <Search />
    <JokesList v-bind:jokes="jokes" />
  </div>
</template>

<script>
import Search from "@/components/Search/Search";
import JokesList from "@/components/JokesList/JokesList";

export default {
  name: "App",
  data() {
    return {
      jokes: [
        { id: 1, title: "Анекдот 1", isLiked: false },
        { id: 1, title: "Анекдот 2", isLiked: false },
        { id: 1, title: "Анекдот 3", isLiked: false },
      ],
    };
  },
  components: {
    Search,
    JokesList,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto 0;
  max-width: 500px;
  border: 1px solid #000;
  padding: 40px;
  box-sizing: border-box;
}
</style>
