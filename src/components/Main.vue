<template>
  <main>
      <Card v-for="movie in movies" :key="movie.id" :movie="movie" />
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
        display: flex;
        flex-wrap: wrap;
    }
</style>