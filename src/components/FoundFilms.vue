<script>
import { store } from "../store";
import SingleCardFilm from "./SingleCardFilm.vue";

export default {
    name: 'FoundFilms',
    components:{
        SingleCardFilm
    },
    data() {
        return {
            store            
        }
    },
}
</script>

<template>
    <div class="container">
        <div class="row justify-content-center gap-3">
            <SingleCardFilm v-for="(elem, index) in store.arrayFoundAll" :key="index" :detailsFilm="elem"/>
        </div>
    </div>
</template>

<style scoped>
    
</style>
