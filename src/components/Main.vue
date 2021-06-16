<template>
  <main>
    <section v-show="movies.length > 0" class="movies">
      <h2>Film:</h2>
      <ul class="cards">
        <li>
          <Card v-for="movie in movies" :key="movie.id" :item="movie" />
        </li>
      </ul>
    </section>
    <section v-show="series.length > 0" class="series">
      <h2>Tv Series:</h2>
      <ul class="cards">
        <li>
          <Card v-for="serie in series" :key="serie.id" :item="serie" />
        </li>
      </ul>
    </section>
  </main>
</template>

<script>
import Card from './Card.vue';


export default {
    name: "Main",
    components: {
        Card
  },
  props: {
    movies: Array,
    series: Array
  }
}
</script>

<style lang="scss" scoped>

@import '~@fortawesome/fontawesome-free/css/all.min.css';

    main {
      text-align: center;
        ul.cards li {
          display: flex;
          flex-wrap: wrap;
          background-color: black;
        }

        h2 {
          color: white;
          text-transform: uppercase;
          margin: 20px 0;

          .fas {
            margin: 0 5px;
            font-size: 20px;
          }
        }

        h3 {
          color: white;
          text-transform: uppercase;
        }
    }
</style>