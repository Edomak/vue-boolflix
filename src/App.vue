<template>
  <div id="app">
    <Header @search="updateSearch" />
    <Main :movies="movies" />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data: function() {
    return {
      apiUrl: "https://api.themoviedb.org/3/search/",
      apiKey: "ee0f54b12ccb8843ee3545b734fca55d",
      query: "",
      movies: [],
    }
  },
  methods: {
    updateSearch(selectFilm) {
      this.query = selectFilm;
    },
    getMovies (search) {
      const apiParams = {
        api_key: this.apiKey,
        query: search,
        language: 'it-IT'
      }
      axios
        .get(this.apiUrl + 'movie', {
          params: apiParams
        })
        .then(
            (res) => {
                this.movies = res.data.results
                console.log(this.movies);
            }
        )
    },
  }
}
</script>

<style lang="scss">
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
</style>
