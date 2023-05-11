<template>
    <nav>
        <div class="container-fluid d-flex justify-content-between">
            <div class="lside d-flex align-items-center">
                <a href=""><img src="/img/netflix-logo-png-2582.png" alt="logo"></a>
                <ul class="d-flex mb-0">
                    <li>
                        <a href="" class="text-light">home</a>
                    </li>
                    <li>
                        <a href="">tv shows</a>
                    </li>
                    <li>
                        <a href="">moviess</a>
                    </li>
                    <li>
                        <a href="">new & popular</a>
                    </li>
                    <li>
                        <a href="">my list</a>
                    </li>
                    <li>
                        <a href="">browse my language</a>
                    </li>
                </ul>
            </div>
            <div class="rside">
                <button class="btn btn-outline-light" type="button" data-bs-toggle="offcanvas" data-bs-target="#offcanvasRight" aria-controls="offcanvasRight"><i class="fa-solid fa-magnifying-glass"></i></button>

                <!-- OffCanvas -->
                <div class="offcanvas offcanvas-end w-75 text-bg-dark" tabindex="-1" id="offcanvasRight" aria-labelledby="offcanvasRightLabel">
                    <div class="offcanvas-header">
                        <h5 class="offcanvas-title" id="offcanvasRightLabel">Ricerca</h5>
                        <button type="button" class="btn-close btn-close-white" data-bs-dismiss="offcanvas" aria-label="Close"></button>
                    </div>

                    <div class="offcanvas-body">
                        <div class="input-group mb-3">
                            <input type="text" class="form-control" placeholder="Cerca film o serie TV" aria-describedby="button-addon2" v-model="store.inputValue">
                            <button class="btn btn-outline-secondary" type="button" id="button-addon2" @click="$emit('search')">Cerca</button>
                        </div>
                        
                        <!-- Carte ricercate dall'utente -->
                        <div class="container-fluid px-4 py-2 text-light">
                            <h3 v-if="store.arrayUserFilms != 0">Film Trovati</h3>
                            <div class="swiper mySwiper">
                              <div class="swiper-wrapper">

                                <TopRatedCardFilm v-for="(elem, index) in store.arrayUserFilms" :key="index" :dettagliFilm="elem"/>
                                
                              </div>
                              <div class="swiper-pagination"></div>
                            </div>
                        </div>
                        
                        <div class="container-fluid px-4 py-2 text-light">
                            <h3 v-if="store.arrayUserTv.length != 0">Serie trovate</h3>
                            <div class="swiper mySwiper">
                              <div class="swiper-wrapper">

                                <TopRatedCardFilm v-for="(elem, index) in store.arrayUserTv" :key="index" :dettagliFilm="elem"/>
                                
                              </div>
                              <div class="swiper-pagination"></div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </nav>
</template>

<script>
import { store } from '../store';
import TopRatedCardFilm from './TopRatedCardFilm.vue';

export default {
    name: 'NavbarComp',
    components:{
        TopRatedCardFilm
    },
    data() {
        return {
            store
        }
    },
    methods: {
        
    },
}
</script>

<style scoped>
nav{
    position: fixed;
    width: 100%;
    top: 0;
    left: 0;
    z-index: 100;
}
    .lside img{
        width: 100px;
    }
    ul li{
        margin-right: 15px;
    }
    ul li a{
        text-decoration: none;
        color: #636363;
        text-transform: capitalize;
    }
    ul li a:hover{
        color: #fff;
    }
    .swiper {
      width: 100%;
      height: 100%;
    }
</style>