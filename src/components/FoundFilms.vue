<script>
import { store } from "../store";
import SingleCardFilm from "./SingleCardFilm.vue";
import SingleCardTv from "./SingleCardTv.vue";

export default {
    name: 'FoundFilms',
    components:{
        SingleCardFilm,
        SingleCardTv
    },
    data() {
        return {
            store
        }
    }
}
</script>

<template>
    <div class="container">
        <!-- Film -->
        <h2 v-if="store.arrayFoundFilms != 0" class="text-light">Film:</h2>
        <div class="row justify-content-center gap-3">
            <SingleCardFilm v-for="(elem, index) in store.arrayFoundFilms" :key="'Film-' + index" :detailsFilm="elem"/>
        </div>
        
        <!-- Serie TV -->
        <h2 v-if="store.arrayFoundFilms != 0" class="text-light">Serie TV:</h2>
        <div class="row justify-content-center gap-3">
            <SingleCardTv v-for="(elem, index) in store.arrayFoundTv" :key="'Tv-' + index" :detailsTv="elem"/>
        </div>

    </div>
</template>

<style scoped>
    
</style>
