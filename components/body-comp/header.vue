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
            <div class="imageSlider">
                <div class="imageSlider-nav">
                    <a class="prev" @click="prev"><img :src="Chevronleft"/></a>
                    <a class="next" @click="next"><img :src="Chevronright"/></a>
                </div>
                <transition-group name="fade" tag="div">
                    <div class="imageSlider-wrapper" v-for="number in [currentNumber]" v-bind:key="number">
                        <img class="imageSlider-item" :src="currentImage.url" @mouseover="stopRotation" @mouseout="startRotation"/>
                    </div>
                </transition-group>
                <ol class="carousel-indicators">
                    <li v-for="(image, index) in images" :key="index" @click="goToSlide(index)" :class="{active: index === currentNumber}">
                        <span></span>
                    </li>
                </ol>
            </div>
        </div>
        <div class="under-carousel-menu">
            <div>
                <div v-for="(uc, index) in undercarousel" v-bind:key="index">
                    <span class="uc-text"><img class="uc-icon" v-bind:src="uc.icon"/>{{ uc.name }}</span>
                </div>
            </div>
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
import Chevronright from '~/assets/assets/icon/chevron-right.svg'
import Chevronleft from '~/assets/assets/icon/chevron-left.svg'

export default {
    name: 'Header',
    data() {
        return {
            BackgroundHead,
            Hero,
            Eduicon,Govericon,Hosicon,Corpicon,Fnbicon,Chevronleft,Chevronright,
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
                { name: "Food & Baverages", icon: Fnbicon},
            ],
            currentNumber: 0,
            timer: null,
        }
    },
    mounted: function() {
        this.startRotation();
    },
    methods: {
        startRotation() {
            this.timer = setInterval(this.next,7000);
        },
        stopRotation() {
            clearTimeout(this.timer);
            this.timer = null;
        },
        next() {
            if(this.currentNumber == this.images.length - 1){
                this.currentNumber = 0;
            } else {
                this.currentNumber++;
            }
        },
        prev() {
            if(this.currentNumber <= 0) {
				this.currentNumber = this.images.length - 1;
			} else {
				this.currentNumber -= 1
			}
        },
        goToSlide(index) {
            this.currentNumber = index;
        }
    },
    computed: {
        currentImage(){
            return this.images[Math.abs(this.currentNumber) % this.images.length];
        },
    },
}
</script>

<style scoped>
.Head-Title{
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
}

.Head-Title-Background{
    position: absolute;
    width: 100%;
    height: 900px;
    top: 0;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: flex-start;
    z-index: -1;
    overflow: hidden;
}

.Head-Title-Text{
    height: 250px;
    width: max-content;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    z-index: 1;
}

.background-right{
    position: relative;
    right: 0;
    background-size: cover;
    background-color: white;
    width: 47%;
    background-size: contain;
}
.background-left{
    position: relative;
    transform: scaleX(-1);
    left: 0;
    width: 47%;
    background-size: contain;
    background-color: white;
}

.Title{
    font-size: 48px;
    font-weight: 700;
    text-align: center;
}
.Desc{
    font-size: 20px;
    font-weight: 400;
    text-align: center;
}

.timer {
  position: absolute;
  bottom: -100px;
}

.imageSlider {
  position: relative;
  display: block;
  width: 100%;
  height: 474px;
}

.imageSlider .imageSlider-nav {
  position: absolute;
  bottom: 0;
  right: 0;
  display: flex;
  border-radius: 10px 0 0 0;
  overflow: hidden;
  z-index: 9;
}

.imageSlider .imageSlider-nav .next,
.imageSlider .imageSlider-nav .prev {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 4.688vw;
  height: 4.688vw;
  background: #02539E;
  opacity: 0.6; 
  color: #4DB6AC;
  cursor: pointer;
}

.imageSlider .imageSlider-nav img{
    width: 4.688vw;
}
.imageSlider .imageSlider-nav .next:hover,
.imageSlider .imageSlider-nav .prev:hover {
  background-color: rgba(255, 255, 255, 0.8);
}



.imageSlider .imageSlider-nav .prev {
  margin-right: 1px;
}

.imageSlider .imageSlider-wrapper {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.imageSlider .imageSlider-item {
  position: relative;
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: 50% 50%;
}

.fade-enter-active,
.fade-leave-active {
  transition: all 0.8s ease;
  overflow: hidden;
  visibility: visible;
  opacity: 1;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
  visibility: hidden;
}

.under-carousel-menu{
    height: 132px;
    background: radial-gradient(50% 2443.21% at 50% 50%, #1D7CD3 0%, #02539E 100%);
    font-weight: 400;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
}

.under-carousel-menu > div{
    width:  83.056vw;
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 20px;
}

.under-carousel-menu > div > div {
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
}

.uc-text{
    font-size: 20px;
    color: white;
    letter-spacing: 0.15px;
    font-weight: 400;
}

.uc-icon{
    width: 27px;
    height: 29.5px;
    margin-right: 0.5vw;
}

.carousel-indicators{
    gap: 24px;
}
.carousel-indicators li{
    width: 72px;
    position: relative;
}

.active{
    background-color: grey;
}

.active span {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 72px;
  height: 5px;
  border-radius: 3px;
  z-index: 100;
  background: white;
  animation: loadingbar 7s ease-in;
}

@keyframes loadingbar {
    0% {
        width: 0;
    }
    100% {
        width: 100%;
    }
}

@media screen and (max-width: 949px) {
    .imageSlider .imageSlider-nav .next, 
    .imageSlider .imageSlider-nav .prev {
        width: 60px;
        height: 60px;
    }
    .under-carousel-menu{
        height: 340px;
    }
    .under-carousel-menu > div{
        justify-content: space-around;
        gap: 30px;
        width: 196px;
    }
    .Head-Title-Text{
        height: max-content;
        padding: 40px 0 40px 0;
    }
}


@media screen and (max-width: 655px) {
    .imageSlider .imageSlider-nav .next, 
    .imageSlider .imageSlider-nav .prev {
        width: 50px;
        height: 50px;
    }
    
    .carousel-indicators{
        position: absolute;
        /* gap: 24px; */
    }
    .carousel-indicators li{
        width: 50px;
    }
    .active span {
        width: 50px;
    }
}

@media screen and (max-width: 512px) {
    .carousel-indicators li{
        width: 20px;
    }
    .active span {
        width: 20px;
    }
}
</style>
