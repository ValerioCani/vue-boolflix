<template>
    <section>
        <div class="SeriesCard" v-for="(series, index) in this.SeriesArray" :key="index">
                <div class="flip-card-inner">
                    <div class="flip-card-front">
                        <img :src="'https://image.tmdb.org/t/p/w342'+ series.poster_path" alt="Avatar">
                    </div>
                    <div class="flip-card-back">
                        <h2>Titolo:</h2>
                        <p>{{series.name}}</p>
                        <h2>Titlo Originale:</h2>
                        <p>{{series.original_name}}</p>
                        <h2>Lingua:</h2>
                        <p v-if="series.original_language=='en'"><img src="@/assets/england.jpg" alt=""></p>
                        <p v-else-if="series.original_language=='de'"><img src="@/assets/germania.jpg" alt=""></p>
                        <p v-else-if="series.original_language=='fr'"><img src="@/assets/france.jpg" alt=""></p>
                        <p v-else-if="series.original_language=='it'"><img src="@/assets/italia.jpg" alt=""></p>
                        <p v-else-if="series.original_language=='cn'"><img src="@/assets/Cina.jpg" alt=""></p>
                        <p v-else-if="series.original_language=='es'"><img src="@/assets/espana.jpg" alt=""></p>
                        <p v-else-if="series.original_language=='ja'"><img src="@/assets/Japan.jpg" alt=""></p>
                        <p v-else-if="series.original_language=='ko'"><img src="@/assets/southkorea.jpg" alt=""></p>
                        <p v-else>{{series.original_language}}</p>
                        <h2>Voto medio della community:</h2>
                        <p class="stars" v-html="starsHTML" :starcounter="StarredVote(series.vote_average)"></p>
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
/* This container is needed to position the front and back side */
.flip-card-inner {
    position: relative;
    width: 100%;
    height: 100%;
    text-align: center;
    transition: transform 0.8s;
    transform-style: preserve-3d;
}

/* Do an horizontal flip when you move the mouse over the flip box container */
.SeriesCard:hover .flip-card-inner {
    transform: rotateY(180deg);
}

/* Position the front and back side */
.flip-card-front, .flip-card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    -webkit-backface-visibility: hidden; /* Safari */
    backface-visibility: hidden;
}

/* Style the front side (fallback if image is missing) */
.flip-card-front {
    background-color: $text_color;
    color: $primary_background_color;
    img{
        width: 100%;
    }
}

/* Style the back side */
.flip-card-back {
    background-color: $primary_background_color;
    color: $text_color;
    transform: rotateY(180deg);
    .stars{
        color:$brand_color;
    }
}
</style>