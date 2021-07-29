<template>
  <div id="app">
    <Search v-on:value="getValue" />
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
      jokes: [],
      jokesDefault: [],
    };
  },
  mounted() {
    fetch("https://v2.jokeapi.dev/joke/Any?type=single&amount=10", {
      headers: {
        "Content-Type": "application/json",
        lang: "en",
      },
    })
      .then((response) => response.json())
      .then((res) => {
        this.jokes = res.jokes.map((item) => {
          item.isLiked = false;
          return item;
        });
        this.jokesDefault = JSON.parse(JSON.stringify(this.jokes));
      });
  },
  methods: {
    getValue(res) {
      console.log(this.jokesDefault);
      if (res === "") {
        this.jokes = this.jokesDefault;
      } else {
        this.jokes = this.jokesDefault.filter((item) => {
          return item.joke.includes(res);
        });
      }
    },
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
