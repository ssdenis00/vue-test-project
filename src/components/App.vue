<template>
  <div id="app">
    <Search />
    <JokesList />
  </div>
</template>

<script>
import Search from "@/components/Search/Search";
import JokesList from "@/components/JokesList/JokesList";

export default {
  name: "App",
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
