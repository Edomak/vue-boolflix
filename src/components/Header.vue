<template>
<header>
    <div class="logo">
        <img src="../assets/logobool2.png" alt="">
    </div>
    <div class="search">
        <input type="text" placeholder="Cerca il titolo di un film" v-model.trim="searchFilm" @keyup.enter="startSearch()">
        <button @click.prevent="startSearch()">Cerca</button>
    </div>
</header>
</template>

<script>
export default {
    name: "Header",
    data: function() {
        return {
            searchFilm: "",
        }
    },
    methods: {
        startSearch() {
            this.$emit("search", this.searchFilm)
            console.log(this.searchFilm);
        }
    }

}
</script>

<style lang="scss" scoped>
    header {
        display: flex;
        justify-content: space-between;
        height: 100px;
        line-height: 100px;
        background-color: black;
    }

    .logo {
        margin: 10px;
    }

    input {
        width: 300px;
        height: 40px;
        border-radius: 8px;
        cursor: pointer;
        margin-right: 10px;
    }

    button {
        width: 80px;
        height: 40px;
        border-radius: 5px;
        cursor: pointer;
        margin-right: 10px;
    }
</style>