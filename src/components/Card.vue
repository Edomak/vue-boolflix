<template>
    <div class="card_box">
        <ul class="card_details">
        <li>
            <p> <strong>Titolo: </strong>{{ movie.title }} {{ movie.name }}</p>
        </li>
        <li> 
            <p> <strong>Titolo originale: </strong> {{ movie.original_title }} {{ movie.original_name }}</p> 
        </li>
        <li> 
            <p> <strong>Lingua: </strong> {{ movie.original_language }} {{ movie.original_language }}</p>
        </li>
        <li>
            <p> <strong>Voto: </strong> {{ movie.vote_average }}</p>
        </li>
    </ul>
    </div>
</template>

<script>
export default {
    name: "Card",
    props: {
    movie: Object,
  }
}
</script>

<style lang="scss" scoped>
    .card_box {
        width: calc(100% / 5);
        padding: 10px 15px;
        border: 1px solid black;

        ul {
            list-style: none;
            li {
                h2 {
                    font-size: 16px;
    
                }
            }
        }
    }
</style>