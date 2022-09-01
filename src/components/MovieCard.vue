<template>
    <section>
        <div class="MovieCard" v-for="(show, index) in this.DataArray" :key="index">
            <div class="flip-card-inner">
                <div class="flip-card-front">
                    <img v-if="(!show.poster_path=='')" :src="'https://image.tmdb.org/t/p/w342'+ show.poster_path" alt="Avatar" >
                    <h2 v-else>Immagine non disponibile</h2>
                </div>
                <div class="flip-card-back">
                    <p>Titolo:</p>
                    <h2 v-if="show.hasOwnProperty('title')">{{show.title}}</h2>
                    <h2 v-else>{{show.name}}</h2>
                    <p>Titlo Originale:</p>
                    <h2 v-if="show.hasOwnProperty('original_title')">{{show.original_title}}</h2>
                    <h2 v-else>{{show.original_name}}</h2>
                    <p>Data di Uscita</p>
                    <h2>{{show.release_date}}</h2>
                    <p>Lingua:</p>
                    <h2 v-if="show.original_language=='en'"><img src="@/assets/england.jpg" alt=""></h2>
                    <h2 v-else-if="show.original_language=='de'"><img src="@/assets/germania.jpg" alt=""></h2>
                    <h2 v-else-if="show.original_language=='fr'"><img src="@/assets/france.jpg" alt=""></h2>
                    <h2 v-else-if="show.original_language=='it'"><img src="@/assets/italia.jpg" alt=""></h2>
                    <h2 v-else-if="show.original_language=='cn'"><img src="@/assets/Cina.jpg" alt=""></h2>
                    <h2 v-else-if="show.original_language=='es'"><img src="@/assets/espana.jpg" alt=""></h2>
                    <h2 v-else-if="show.original_language=='ja'"><img src="@/assets/Japan.jpg" alt=""></h2>
                    <h2 v-else-if="show.original_language=='ko'"><img src="@/assets/southkorea.jpg" alt=""></h2>
                    <h2 v-else>{{show.original_language}}</h2>
                    <p>Voto medio della community:</p>
                    <h2 class="stars" v-html="StarredVote(show.vote_average)"></h2>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
export default {
    name:'MovieCard',
    props:{
        DataArray:Array
    },
    methods:{
        StarredVote(votenumber){
            let starsHTML="";
            let starcounter=Math.ceil(votenumber / 2);
            for(let i=0; i<starcounter; i++){
                starsHTML += '<i class="fa-solid fa-star"></i>';
            }
            for(let i=starcounter; i<5; i++){
                starsHTML += '<i class="fa-regular fa-star"></i>';
            }
            return starsHTML
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
    .MovieCard{
        perspective: 1000px;
        margin: 50px 10px;
        width: 300px;
        height: 450px;
        background-color: $secondary_background_color;
    }
}
</style>