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
  created() {
    this.objectHero()
  },
  methods: {
    SearchFilmApi(){
      axios.all([
        axios.get(`https://api.themoviedb.org/3/search/movie?api_key=ab42a7864ebdef8b4e338a6d3256ad1d&language=it-IT&query=${store.inputValue}`),
        axios.get(`https://api.themoviedb.org/3/search/tv?api_key=ab42a7864ebdef8b4e338a6d3256ad1d&language=it-IT&query=${store.inputValue}`)
      ])
      .then(axios.spread((res1, res2) =>{
        store.arrayUserFilms = res1.data.results;
        store.arrayUserTv = res2.data.results;

       }))
     },

    objectHero(){
      const options = {
          method: 'GET',
          url: 'https://api.themoviedb.org/3/movie/popular',
          params: {language: 'it-IT', page: '1'},
          headers: {
            accept: 'application/json',
            Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJhYjQyYTc4NjRlYmRlZjhiNGUzMzhhNmQzMjU2YWQxZCIsInN1YiI6IjY0NWEwZDQ3NzdkMjNiMDEzNjVlMGIwMyIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.mYd5rop0tYeLWKBkDdnvoCxcISNFbGKjoDKSAFj_Q8E'
          }
        };

        axios
          .request(options)
          .then(function (response) {
            store.objectHero = response.data.results[0];
            console.log(response.data.results[0])
          })
          .catch(function (error) {
            console.error(error);
          });
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