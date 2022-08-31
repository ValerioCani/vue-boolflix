<template>
    <section>
        <div class="SeriesCard" v-for="(series, index) in this.SeriesArray" :key="index">
                <div class="flip-card-inner">
                    <div class="flip-card-front">
                        <img :src="'https://image.tmdb.org/t/p/w342'+ series.poster_path" alt="Avatar">
                    </div>
                    <div class="flip-card-back">
                        <p>Titolo:</p>
                        <h2>{{series.name}}</h2>
                        <p>Titlo Originale:</p>
                        <h2>{{series.original_name}}</h2>
                        <p>Lingua:</p>
                        <h2 v-if="series.original_language=='en'"><img src="@/assets/england.jpg" alt=""></h2>
                        <h2 v-else-if="series.original_language=='de'"><img src="@/assets/germania.jpg" alt=""></h2>
                        <h2 v-else-if="series.original_language=='fr'"><img src="@/assets/france.jpg" alt=""></h2>
                        <h2 v-else-if="series.original_language=='it'"><img src="@/assets/italia.jpg" alt=""></h2>
                        <h2 v-else-if="series.original_language=='cn'"><img src="@/assets/Cina.jpg" alt=""></h2>
                        <h2 v-else-if="series.original_language=='es'"><img src="@/assets/espana.jpg" alt=""></h2>
                        <h2 v-else-if="series.original_language=='ja'"><img src="@/assets/Japan.jpg" alt=""></h2>
                        <h2 v-else-if="series.original_language=='ko'"><img src="@/assets/southkorea.jpg" alt=""></h2>
                        <h2 v-else>{{series.original_language}}</h2>
                        <p>Voto medio della community:</p>
                        <h2 class="stars" v-html="starsHTML" :starcounter="StarredVote(series.vote_average)"></h2>
                    </div>
                </div>
        </div>
    </section>
</template>

<script>
export default {
    name:'seriesCard',
    props:{
        SeriesArray:Array
    },
    data(){
        return{
            starsHTML:"",
        }
    },
    methods:{
        StarredVote(votenumber){
            this.starsHTML="";
            let starcounter=Math.ceil(votenumber / 2);
            for(let i=0; i<starcounter; i++){
                this.starsHTML += '<i class="fa-solid fa-star"></i>';
            }
            for(let i=starcounter; i<5; i++){
                this.starsHTML += '<i class="fa-regular fa-star"></i>';
            }
        }
    }
}
</script>

<style scoped lang="scss">
@import '../styles/general.scss';
@import '../styles/var.scss';
section{
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
    .SeriesCard{
        perspective: 1000px;
        width: 300px;
        height: 450px;
        background-color: $secondary_background_color;
        margin: 50px 10px;
    }
}
</style>