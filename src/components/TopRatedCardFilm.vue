<template>
    <div class="swiper-slide card">
        <div class="card-img">
            <img :src="(dettagliFilm.poster_path != null) ?`https://image.tmdb.org/t/p/w500${dettagliFilm.poster_path}` : '/img/netflix-logo-png-2582.png'" :alt="dettagliFilm.title">
        </div>
        <div class="card-info">
            <h3 class="mb-0">{{ dettagliFilm.title }}</h3>
            <span class="d-block" v-if="dettagliFilm.release_date = dettagliFilm.release_date">Anno di rilascio: {{ dettagliFilm.release_date }}</span>

            <!-- Stelline -->
            <div class="stars-outer">
                <div class="stars-inner" :style="GetAverage()"></div>
            </div>
        </div>
    </div>
</template>

<script>
export default{
    name: 'TopRatedCardFilm',
    props: ['dettagliFilm'],
    methods: {
        GetAverage(){
            const starsTotal = 5

            let starPercentage = (this.dettagliFilm.vote_average / starsTotal) * 100;

            let starPercentageRounded = `${Math.round(starPercentage / 10) * 10}%`;

            let stringa = `width: ${starPercentageRounded}`

            return stringa
        }
    },
}
</script>

<style scoped>
    .card{
        border: transparent;
        background-color: #131313;
        position: relative;
    }
    .card img{
        display: block;
        width: 100%;
        height: 100%;
        object-fit: cover;
        object-position: center;
        background-color: #131313;
    }
    .card-info{
        display: none;
        position: absolute;
        bottom: 10%;
        left: 5px;
        color: white;
    }
    .card:hover .card-info{
        display: block;
    }
    .card:hover img{
        opacity: 0.2;
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