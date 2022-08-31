<template>
    <main>
        <h2>Film</h2>
        <MovieCard class="card" :MoviesArray="this.MoviesArray"/>
        <div class="divisor"></div>
        <h2>Serie TV</h2>
        <SeriesCard class="card" :SeriesArray="this.SeriesArray"/>
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
        color: $brand_color;
        font-size: 40px;
        text-transform: uppercase;
    }
    .divisor{
        border:solid 3px $primary_background_color;
    }
    .card{
        cursor: pointer;
    }
}
</style>