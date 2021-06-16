<template>
    <div class="card_box">
        <!-- Poster -->
        <div class="poster">
            <img 
            v-if="item.poster_path" 
            :src="`https://image.tmdb.org/t/p/w342${item.poster_path}`" 
            alt="poster movie">
            <img class="unavailable" v-else src="@/assets/unavaible.jpeg" alt="Poster Unavailable">
        </div>
        <!-- /Poster -->
        <ul class="card_details overlay">
        <!-- Title -->
        <li class="title">
            <p><strong>Titolo: </strong>{{ item.title ? item.title : item.name }}</p>
        </li>
        <!-- /Title -->
        <!-- Original title -->
        <li class="original_title"> 
            <p><strong>Titolo originale: </strong> {{ item.original_title ? item.original_title : item.original_name }}</p> 
        </li>
        <!-- /Original title -->
        <!-- Language -->
        <li class="language"> 
            <strong>Lingua: </strong>
            <img v-if="isFlag(item.original_language)"  
            :src="require(`@/assets/${item.original_language}.png`)" 
            :alt="item.original_language" class="flag">
            <span v-else>{{ item.original_language }}</span>
        </li>
        <!-- /Language -->
        <!-- Overview -->
        <!-- <li class="overview">
            <p>{{ movie.overview }}</p>
        </li> -->
        <!-- /Overview -->
        <!-- Vote -->
        <li class="vote">
            <strong>Voto: </strong>
            <span>
                <i v-for="(star, index) in starVote(item.vote_average)" :key="index" class="fas fa-star"></i>
                </span>
            <span>
                <i v-for="(star, index) in 5 - starVote(item.vote_average)" :key="index" class="far fa-star"></i>
            </span>
        </li>
        <!-- /Vote -->
        </ul>
    </div>
</template>

<script>

export default {
    name: "Card",
    props: {
    item: Object
  },
  data: function () {
     return {
         flagsImg: ['it', 'en'],
     }
  },
  methods: {
    isFlag(language) {
        return this.flagsImg.includes(language);
    },
    starVote (vote) {
        return Math.ceil(vote / 2);
    }
  }
}
</script>

<style lang="scss" scoped>

@import '~@fortawesome/fontawesome-free/css/all.min.css';

    .card_box {
        width: calc(100% / 5);
        padding: 10px 10px;

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
            width: 250px;
            height: 350px;
            border-radius: 5px;
            cursor: pointer;
        }

        .vote > span {
            font-size: 10px;
            margin: 3px 0;
            color: yellow;
        }
    }
</style>