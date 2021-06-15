<template>
  <main>
    <div v-if="movies.length > 0" class="cards">
        <Card v-for="movie in movies" :key="movie.id" :movie="movie" />
    </div>
      <h2 v-else>Non ci sono risultati per la tua ricerca</h2>
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
  }
}
</script>

<style lang="scss" scoped>
    main {
      text-align: center;
        .cards {
          display: flex;
          flex-wrap: wrap;
          background-color: black;
        }

        h2 {
          color: white;
          text-transform: uppercase;
          margin: 100px 0;
        }
    }
</style>