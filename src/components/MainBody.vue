<template>
    <main>
        <MovieCard :MoviesArray="this.MoviesArray"/>
    </main>
</template>

<script>
import MovieCard from './MovieCard.vue'
export default {
    name:'MainBody',
    components:{
       MovieCard 
    },
    props:{
        MoviesArray:Array
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