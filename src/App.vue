<template>
  <div id="app">
    <Header @search="updateSearch" />
    <Main :movies="movies" :series="series" />
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
  data: function () {
    return {
      apiUrl: "https://api.themoviedb.org/3/search/",
      apiKey: "ee0f54b12ccb8843ee3545b734fca55d",
      query: "",
      movies: [],
      series: []
    }
  },
  methods: {
    updateSearch(selectFilm) {
      this.query = selectFilm;
      this.getMovies();
      this.getSeries();
    },
    getMovies() {
      const apiParams = {
        api_key: this.apiKey,
        query: this.query,
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
    getSeries() {
      const apiParams = {
        api_key: this.apiKey,
        query: this.query,
        language: 'it-IT'
      }
      axios
        .get(this.apiUrl + 'tv', {
          params: apiParams
        })
        .then(
            (res) => {
                this.series = res.data.results
                console.log(this.series);
            }
        )
    },
  }
}
</script>

<style lang="scss">

@import '~@fortawesome/fontawesome-free/css/all.min.css';

  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    background-color: black;
  }
  main {
    width: 95%;
    margin: 0 auto;
  }
</style>
