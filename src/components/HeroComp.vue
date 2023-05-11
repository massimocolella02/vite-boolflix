<template>
    <div class="container-fluid m-0 p-0 position-relative d-flex align-items-center" id="hero">
        <div class="hero-img h-100">
            <img class="position-absolute w-100 h-100 object-fit-cover" :src="`https://image.tmdb.org/t/p/original${store.objectHero.backdrop_path}`" :alt="store.objectHero.title">
        </div>
        <div class="hero-info ms-4 w-50">
            <h2>{{ store.objectHero.title }}</h2>
            <div class="stars-outer">
                <div class="stars-inner" :style="GetAverage()"></div>
            </div>
            <p>{{ store.objectHero.overview }}</p>
            <button class="btn btn-outline-light me-3"><i class="fa-solid fa-play"></i> Play</button>
            <button class="btn btn-outline-light"><i class="fa-solid fa-circle-info"></i> Più Info</button>
        </div>

    </div>
</template>

<script>
import { store } from "../store";

export default {
    name: 'HeroComp',
    data() {
        return {
            store
        }
    },
    methods: {
        GetAverage(){
            const starsTotal = 5

            let starPercentage = (store.objectHero.vote_average / starsTotal) * 100;

            let starPercentageRounded = `${Math.round(starPercentage / 10) * 10}%`;

            let stringa = `width: ${starPercentageRounded}`

            return stringa
        }
    },
}
</script>

<style scoped>
    #hero{
        height: 540px;
        color: #fff;
    }
    .hero-img img{
        object-position: center;
        z-index: -1;
        background-color: rgba(13, 13, 13, 0.3);
    }
    .stars-outer {
    position: relative;
    display: inline-block;
}
.stars-inner {
    position: absolute;
    top: 0;
    left: 0;
    white-space: nowrap;
    overflow: hidden;
}
.stars-outer::before {
    content: "\f005 \f005 \f005 \f005 \f005";
    font-family: "Font Awesome 5 Free";
    font-weight: 900;
    color: #ccc;
}
.stars-inner::before {
    content: "\f005 \f005 \f005 \f005 \f005";
    font-family: "Font Awesome 5 Free";
    font-weight: 900;
    color: #f8ce0b;
}
</style>