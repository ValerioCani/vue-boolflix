<template>
    <main>
        <MovieCard :MoviesArray="this.MoviesArray"/>
        <SeriesCard :MoviesArray="this.SeriesArray"/>
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
}
</style>