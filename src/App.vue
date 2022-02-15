<template>
  <div id="app">
    <Header :movies="movies" @pass-search="search" />
    <Main :movies="movies" :series="series" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      movies: [],
      series: [],
      api_moviedb: {
        language: "it-IT",
        baseUri: "https://api.themoviedb.org/3",
        key: "4dddbdfa5994addeb864ece0b1011f23",
      },
    };
  },
  methods: {
    search(choice) {
      console.log(choice);
      if (!choice) {
        this.movies = [];
        this.series = [];
        return;
      }
      const { key, language } = this.api_moviedb;
      const config = {
        params: {
          api_key: key,
          language,
          query: choice,
        },
      };
      this.fetchAPI("search/movie", config, "movies");
      this.fetchAPI("search/tv", config, "series");
    },
    fetchAPI(endpoint, config, target) {
      axios
        .get(`${this.api_moviedb.baseUri}/${endpoint}`, config)
        .then((res) => {
          this[target] = res.data.results;
          console.log(this[target]);
        });
    },
  },
};
</script>

<style lang="scss">
@import "./assets/sass/style.scss";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
