<script>
import axios, { Axios } from 'axios';
import { store } from './store';
import NavbarComp from './components/NavbarComp.vue'
import HeroComp from './components/HeroComp.vue'
import TopRated from './components/TopRated.vue'

export default {
  name: 'App',
  components:{
    NavbarComp,
    HeroComp,
    TopRated
  },
  data() {
    return {
      store  
    }
  },
  methods: {
    SearchFilmApi(){
      axios.all([
        axios.get(`https://api.themoviedb.org/3/search/movie?api_key=ab42a7864ebdef8b4e338a6d3256ad1d&language=it_IT&query=${store.inputValue}`),
        axios.get(`https://api.themoviedb.org/3/search/tv?api_key=ab42a7864ebdef8b4e338a6d3256ad1d&language=it_IT&query=${store.inputValue}`)
      ])
      .then(axios.spread((res1, res2) =>{
        store.arrayUserFilms = res1.data.results;
        store.arrayUserTv = res2.data.results;

        console.log(store.arrayUserTv)
       }))
     }
  }
}
</script>

<template>
  <header>
    <NavbarComp @search="SearchFilmApi()"/>
    <HeroComp/>
  </header>
  <main>
    <TopRated/>
  </main>
</template>

<style>
main{
  background-color: #131313;
}
</style>