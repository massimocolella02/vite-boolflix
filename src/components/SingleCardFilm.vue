<script>
export default {
    name: 'SingleCardFilm',
    props: ['detailsFilm'],
    methods:{
        GetAverage(){
            let film_average = this.detailsFilm.vote_average
            const starsTotal = 5

            let starPercentage = (this.detailsFilm.vote_average / starsTotal) * 100;

            let starPercentageRounded = `${Math.round(starPercentage / 10) * 10}%`;

            let stringa = `width: ${starPercentageRounded}`

            return stringa
        }
    }
}
</script>

<template>
    <div class="card col-3">
        <img :src="'https://image.tmdb.org/t/p/original' + detailsFilm.poster_path" class="card-img-top" :alt="detailsFilm.title">
        <div class="card-body">
            <h5 class="card-title">{{ detailsFilm.title }}</h5>
            <p class="card-text">{{ detailsFilm.overview }}</p>

            <div class="stars-outer">
                <div class="stars-inner" :style="GetAverage()"></div>
            </div>
        </div>
    </div>
</template>

<style scoped>
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