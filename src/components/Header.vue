<template>
<header>
    <div class="logo">
        <a href="#"><img src="../assets/logobool2.png" alt="boolflix Logo"></a> 
    </div>
    <div class="search">
        <input type="text" placeholder="Cerca il titolo di un film" v-model.trim="searchFilm" @keyup.enter="startSearch()">
        <button @click="startSearch">Cerca</button>
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
        },
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
        margin: 15px;
    }

    input {
        width: 300px;
        height: 40px;
        border-radius: 8px;
        cursor: pointer;
        margin-right: 15px;

        &[placeholder] {
            padding-left: 10px;
            font-size: 16px;
        }
    }

    button {
        width: 80px;
        height: 40px;
        border-radius: 5px;
        cursor: pointer;
        margin-right: 10px;
        text-transform: uppercase;

        &:hover {
            color: red;
            border: 1px solid red;
        }
    }
</style>