<template>
    <div class="card_box">
        <!-- Poster -->
        <div class="poster">
            <img 
            v-if="movie.poster_path" 
            :src="`https://image.tmdb.org/t/p/w342${movie.poster_path}`" 
            alt="poster movie">
            <img class="unavailable" v-else src="@/assets/unavaible.jpeg" alt="Poster Unavailable">
        </div>
        <!-- /Poster -->
        <ul class="card_details">
        <!-- Title -->
        <li class="title">
            <p> <strong>Titolo: </strong>{{ movie.title }} {{ movie.name }}</p>
        </li>
        <!-- /Title -->
        <!-- Original title -->
        <li class="original_title"> 
            <p> <strong>Titolo originale: </strong> {{ movie.original_title }} {{ movie.original_name }}</p> 
        </li>
        <!-- /Original title -->
        <!-- Language -->
        <li class="language"> 
            <strong>Lingua: </strong>
            <img v-if="isFlag(movie.original_language)"  
            :src="require(`@/assets/${movie.original_language}.png`)" 
            :alt="movie.original_language" class="flag">
            <span v-else>{{ movie.original_language }}</span>
        </li>
        <!-- /Language -->
        <!-- Overview -->
        <!-- <li class="overview">
            <p>{{ movie.overview }}</p>
        </li> -->
        <!-- /Overview -->
        <!-- Vote -->
        <li class="vote">
            <p> <strong>Voto: </strong> {{ movie.vote_average }}</p>
        </li>
        <!-- /Vote -->
        </ul>
    </div>
</template>

<script>
export default {
    name: "Card",
    props: {
    movie: Object,
  },
  data: function () {
     return {
         flagsImg: ['it', 'en'],
     }
  },
  methods: {
      isFlag(language) {
            return this.flagsImg.includes(language);
        }
  }
}
</script>

<style lang="scss" scoped>
    .card_box {
        width: calc(100% / 6);
        padding: 10px 10px;
        border: 1px solid black;

        // .card_details {
        //     display: none;
        // }

        ul {
            list-style: none;
        }
        p,
        span {
            font-size: 15px;
            color: white;
        }
        strong {
            color:gray;
            font-weight: bolder;
        }

        .language > img {
            height: 10px;

        }

        .poster img {
            width: 200px;
            height: 300px;
            border-radius: 5px;
            cursor: pointer;
        }
    }
</style>