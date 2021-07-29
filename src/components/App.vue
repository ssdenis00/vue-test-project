<template>
  <div id="app">
    <Search v-on:value="searchForJokes" />
    <JokesList v-bind:jokes="jokes" @handleLikeClick="getLikedJokes" />
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
      isLiked: [],
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
        // добавляю свойство для лайков в каждый объект массива
        this.jokes = res.jokes.map((item) => {
          //
          item.isLiked = false;
          return item;
        });

        // создал дубликат объекта, для того чтобы возвращать его при удалении строки с инпута.
        this.jokesDefault = JSON.parse(JSON.stringify(this.jokes));
      });
  },
  methods: {
    // поиск по слову
    searchForJokes(res) {
      if (res === "") {
        this.jokes = this.jokesDefault;
      } else {
        this.jokes = this.jokesDefault.filter((item) => {
          return item.joke.includes(res);
        });
      }
    },
    // добавляю залайканый анекдот
    getLikedJokes(item) {
      this.isLiked = [...this.isLiked, item];
      console.log(this.isLiked);
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
