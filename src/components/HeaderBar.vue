<template>
    <header>
        <h1>BOOLFLIX</h1>
        <div>
            <label for="searchbar">Cerca i tuoi Film Preferiti</label>
            <input type="text" id="searchbar" v-model="MovieSearch">
            <button @click="$emit('SearchInput', MovieSearch)"><i class="fa-solid fa-magnifying-glass"></i></button>
        </div>
    </header>
</template>

<script>
export default {
    name:'HeaderBar',
    data(){
        return{
            MovieSearch:"",
        }
    }
}
</script>

<style scoped lang="scss">
@import '../styles/general.scss';
@import '../styles/var.scss';
header{
    height: 90px;
    background-color: $primary_background_color;
    color: $brand_color;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 20px;
    label{
        color: $text_color;
        margin-right: 10px;
    }
    input{
        height: 30px;
        padding: 10px;
        font-weight: bold;
    }
    button{
        width: 100px;
        height: 30px;
        cursor: pointer;
    }
}
</style>