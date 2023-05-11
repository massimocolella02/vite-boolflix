<template>
    <div class="container-fluid m-0 p-0 position-relative d-flex align-items-center" id="hero">
        <div class="hero-img h-100">
            <img class="position-absolute w-100 h-100 object-fit-cover" src="https://media-assets.wired.it/photos/61a5ee5093eea711c1e28468/4:3/w_924,h_693,c_limit/casa-carta-4.jpeg" alt="immagine-hero">
        </div>
        <div class="hero-info ms-4 w-50">
            <h2>Titolo</h2>
            <span>Stelline</span>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum vero dignissimos rem, iure quos odit unde recusandae excepturi adipisci quas ipsum vitae officia atque ea illum repellendus laudantium sed quod!</p>
            <button class="btn btn-outline-light me-3"><i class="fa-solid fa-play"></i> Play</button>
            <button class="btn btn-outline-light"><i class="fa-solid fa-circle-info"></i> Più Info</button>
        </div>

    </div>
</template>

<script>
export default {
    
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
</style>