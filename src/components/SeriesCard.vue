<template>
    <section>
        <div class="SerisCard" v-for="(series, index) in this.SeriesArray" :key="index">
            <h2>Titolo:</h2>
            <p>{{series.name}}</p>
            <h2>Titlo Originale:</h2>
            <p>{{series.original_title}}</p>
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
            <p>{{series.vote_average}}</p>
        </div>
    </section>
</template>

<script>
export default {
    name:'seriesCard',
    props:{
        SeriesArray:Array
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
    .SerisCard{
        width: 300px;
        height: 400px;
        background-color: rebeccapurple;
        margin: 10px;
    }
}
</style>