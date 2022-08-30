<template>
  <div id="app">
    <HeaderBar @SearchInput="ApiCreator"/>
    <MainBody :MoviesArray="this.FilmObjectArray"/>
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
      apiToSearch:"",
      FilmObjectArray:[],
    }
  },
  methods:{
    ApiCreator(SearchString){
      this.apiToSearch='https://api.themoviedb.org/3/search/movie?api_key=f97c51adbea6b8bac5f39b824003cd49&query='+SearchString+'&language=it-IT';
      console.log(this.apiToSearch)
      axios.get(this.apiToSearch)
      .then(severAnswer => {
      this.FilmObjectArray = severAnswer.data.results;
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
