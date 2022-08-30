<template>
    <main>
        <h2>Film</h2>
        <MovieCard :MoviesArray="this.MoviesArray"/>
        <h2>Serie TV</h2>
        <SeriesCard :SeriesArray="this.SeriesArray"/>
    </main>
</template>

<script>
import MovieCard from './MovieCard.vue'
import SeriesCard from './SeriesCard.vue'
export default {
    name:'MainBody',
    components:{
       MovieCard,
       SeriesCard
    },
    props:{
        MoviesArray:Array,
        SeriesArray:Array
    }
}   
</script>

<style scoped lang="scss">
@import '../styles/general.scss';
@import '../styles/var.scss';
main{
    height:100%;
    background-color: $secondary_background_color;
    text-align: center;
    h2{
        color: $text_color;
    }
}
</style>