<template>
    <div class="container-fluid px-4 py-2 text-light" id="top-rated">
        <h2>Top Rated</h2>
        <div class="swiper mySwiper">
          <div class="swiper-wrapper">
            <TopRatedCardFilm v-for="(elem, index) in store.arrayTopRatedFilm" :key="'TRFilm-'+index" :dettagliFilm="elem"/>
          </div>
          <div class="swiper-pagination"></div>
        </div>
    </div>
</template>
<script>
import TopRatedCardFilm from './TopRatedCardFilm.vue'
import axios from 'axios';
import { store } from '../store'

export default {
    name: 'TopRated',
    components:{
      TopRatedCardFilm
    },
    data() {
      return {
        store
      }
    },
    created() {
      this.callApi()
    },
    methods: {
      callApi(){

        //Opzioni per topr rated film
        const options = {
            method: 'GET',
            url: 'https://api.themoviedb.org/3/movie/top_rated',
            params: {language: 'it-IT', page: '1'},
            headers: {
              accept: 'application/json',
              Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJhYjQyYTc4NjRlYmRlZjhiNGUzMzhhNmQzMjU2YWQxZCIsInN1YiI6IjY0NWEwZDQ3NzdkMjNiMDEzNjVlMGIwMyIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.mYd5rop0tYeLWKBkDdnvoCxcISNFbGKjoDKSAFj_Q8E'
            }
          };
            axios
            .request(options)
            .then(function(response) {
              store.arrayTopRatedFilm = response.data.results;
            })
            .catch(function (error) {
              console.error(error);
            });
        
            
      }
    }
}
</script>

<style scoped>
    .swiper {
      width: 100%;
      height: 100%;
    }
</style>