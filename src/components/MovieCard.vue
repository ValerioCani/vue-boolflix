<template>
    <section>
        <div class="card" v-for="(movie, index) in this.MoviesArray" :key="index">
            <h2>Titolo:</h2>
            <p>{{movie.title}}</p>
            <h2>Titlo Originale:</h2>
            <p>{{movie.original_title}}</p>
            <h2>Lingua:</h2>
            <p>{{movie.original_language}}</p>
            <h2>Voto medio della community:</h2>
            <p>{{movie.vote_average}}</p>

        </div>
    </section>
</template>

<script>
export default {
    name:'MovieCard',
    props:{
        MoviesArray:Array
    },
}
</script>

<style scoped lang="scss">
@import '../styles/general.scss';
@import '../styles/var.scss';
section{
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
    .card{
        width: 300px;
        height: 400px;
        background-color: aqua;
        margin: 10px;
    }
}
</style>