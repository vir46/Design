<template>
    <div id="Body-Header">
        <div class="Head-Title">
            <div class="Head-Title-Background">
                <img :src="BackgroundHead" class="background-left" alt="">
                <img :src="BackgroundHead" class="background-right" alt="">
            </div>
            <div class="Head-Title-Text">
                <span class="Title">Digital Service Provider</span>
                <span class="Desc">Satu Solusi Untuk Semua Kebutuhan Digital Anda</span>
            </div>
        </div>
        <div>
            <b-carousel
                id="carousel-no-animation carouselhead"
                indicators
                controls
                class="carousel slide" data-bs-ride="carousel"
            >
                <b-carousel-slide
                    v-for="(image, index) in images"
                    v-bind:key="'A'+ index"
                    v-bind:img-src="image.url"
                ></b-carousel-slide>
                
            </b-carousel>
        </div>
        <div class="under-carousel-menu">
            <span class="uc-text" v-for="(uc, index) in undercarousel" v-bind:key="'B'+ index"><img class="uc-icon" v-bind:src="uc.icon"/>{{ uc.name }}</span>
        </div>
    </div>
</template>

<script>
import BackgroundHead from '../../assets/assets/bg-layout.svg'
import Hero from '~/assets/assets/image/hero.png'
import Eduicon from '../../assets/assets/icon/education.svg'
import Govericon from '../../assets/assets/icon/government.svg'
import Hosicon from '../../assets/assets/icon/hospitality.svg'
import Corpicon from '../../assets/assets/icon/corporate.svg'
import Fnbicon from '../../assets/assets/icon/food-baverages.svg'

export default {
    name: 'Header',
    data() {
        return {
            BackgroundHead,
            Hero,
            Eduicon,Govericon,Hosicon,Corpicon,Fnbicon,
            images: [
                { url: Hero},
                { url: Hero},
                { url: Hero},
                { url: Hero},
            ],
            undercarousel: [
                { name: "Education", icon: Eduicon},
                { name: "Government", icon: Govericon},
                { name: "Hospitality", icon: Hosicon},
                { name: "Corporate", icon: Corpicon},
                { name: "Food & Beverages", icon: Fnbicon},
            ]
        }
    }
}
</script>

<style scoped>
.Head-Title{
    display: flex;
    align-items: center;
    justify-content: center;
}

.Head-Title-Background{
    position: absolute;
    width: 100%;
    top: 0;
    left: 0;
    display: flex;
    flex-direction: row;
}

.Head-Title-Text{
    height: 350px;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    z-index: 1;
}

.background-right{
    display: block;
    background-size: cover;
    background-color: white;
    width: 50%;
    height: 100%;
    background-size: cover;
    z-index: -1;
}
.background-left{
    display: block;
    -webkit-transform: scaleX(-1);
    transform: scaleX(-1);
    width: 50%;
    background-size: cover;
    background-color: white;
    height: 100%;
    background-size: cover;
    z-index: -1;
}

.Title{
    font-size: 48px;
    font-weight: 700;
}
.Desc{
    font-size: 20px;
    font-weight: 400;
}
.carousel-image{
    height: 474px;
}

.under-carousel-menu{
    height: 132px;
    background: radial-gradient(50% 2443.21% at 50% 50%, #1D7CD3 0%, #02539E 100%);
    font-weight: 400;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    gap: 10%;
}

.uc-text{
    /* margin: 0 40px 0 40px; */
    font-size: 20px;
    color: white;
}

.uc-icon{
    /* margin-right: 5px; */
    width: 27px;
    height: 29.5px;
}

</style>
