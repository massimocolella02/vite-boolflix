<script>
import { store } from "../store";
export default {
    name: 'SearchComp',
    data() {
        return {
            store            
        }
    },
}
</script>

<template>
    <div class="input-group mb-3 w-50 m-auto">
        <input type="text" class="form-control" placeholder="Inserisci il nome di un film" aria-label="Inserisci il nome di un film" aria-describedby="button-addon2" v-model="store.nameFilm">
        <button class="btn btn-outline-secondary" type="button" id="button-addon2" @click="$emit('searchFilm')">Cerca</button>
    </div>
</template>

<style scoped>
    
</style>