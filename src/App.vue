<template>
  <div id="app">
    <HeaderBar @SearchInput="ApiCreator"/>
    <MainBody :MoviesArray="this.FilmObjectArray" :SeriesArray="this.SeriesObjectArray"/>
  </div>
</template>

<script>
import axios from 'axios';
import HeaderBar from './components/HeaderBar.vue';
import MainBody from './components/MainBody.vue';

export default {
  name: 'App',
  components: {
    HeaderBar,
    MainBody
  },
  data(){
    return{
      MoviesapiToSearch:"",
      SeriesapiToSearch:"",
      FilmObjectArray:[],
      SeriesObjectArray:[],
    }
  },
  methods:{
    ApiCreator(SearchString){
      this.MovieApiCreator(SearchString);
      this.SeriesApiCreator(SearchString);
    },
    MovieApiCreator(SearchString){
      this.MoviesapiToSearch='https://api.themoviedb.org/3/search/movie?api_key=f97c51adbea6b8bac5f39b824003cd49&query='+SearchString+'&language=it-IT';
      console.log(this.MoviesapiToSearch)
      axios.get(this.MoviesapiToSearch)
      .then(severAnswer => {
      this.FilmObjectArray = severAnswer.data.results;
      })
    },
    SeriesApiCreator(SearchString){
      this.SeriesapiToSearch='https://api.themoviedb.org/3/search/tv?api_key=f97c51adbea6b8bac5f39b824003cd49&query='+SearchString+'&language=it-IT';
      console.log(this.SeriesapiToSearch)
      axios.get(this.SeriesapiToSearch)
      .then(severAnswer => {
      this.SeriesObjectArray = severAnswer.data.results;
      })
    }
  },
}
</script>

<style lang="scss">
@import '~@fortawesome/fontawesome-free/css/all.css';
@import './styles/general.scss';
@import './styles/var.scss';
</style>
