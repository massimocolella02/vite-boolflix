<script>
import axios, { Axios } from 'axios';
import { store } from './store';
import SearchComp from './components/SearchComp.vue';
import FoundFilms from './components/FoundFilms.vue';

export default {
  name: 'App',
  components:{
    SearchComp,
    FoundFilms
  },
  data() {
    return {
      store  
    }
  },
  methods: {
    SearchFilmApi(){
      axios.all([
        axios.get(`https://api.themoviedb.org/3/search/movie?api_key=ab42a7864ebdef8b4e338a6d3256ad1d&language=it_IT&query=${store.nameFilm}`),
        axios.get(`https://api.themoviedb.org/3/search/tv?api_key=ab42a7864ebdef8b4e338a6d3256ad1d&language=it_IT&query=${store.nameFilm}`)
      ])
      .then(axios.spread((res1, res2) =>{
        const films_found = res1.data.results;
        const tv_found = res2.data.results;
        
        store.arrayFoundFilms = films_found;
        store.arrayFoundTv = tv_found;
      }))
    }
  }
}
</script>

<template>
  <div id="netflix" class="overflow-auto">
    <SearchComp @searchFilm="SearchFilmApi()"/>
    <FoundFilms/>
  </div>
</template>

<style>
  #netflix{
    height: 100vh;
    background-color: black;
  }
</style>