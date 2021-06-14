<template>
    <div class="card_box">
        <ul class="card_details">
        <li>
            <h2>Titolo: {{ movie.title }}</h2>
        </li>
        <li> 
            <h2>Titolo originale:</h2> 
        </li>
        <li> 
            <h2>Lingua:</h2>
        </li>
        <li>
            <h2>Voto:</h2>
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
    }
</style>