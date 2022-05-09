<template>
    <div id="content3">
        <div class="content-titles">
            <span class="content-title">Aktivitas Sarat Manfaat</span>
            <span class="content-title-desc">Potret beragam aktivitas sarat manfaat</span>
        </div>
        <div class="content-card">
            <img :src="ImageBibit" class="content-card-background"/>
            <div class="imageSlider-nav" @mouseover="stopRotation" @mouseout="startRotation">
                        <a class="prev" @click="prev"><img :src="Chevronleft"/></a>
                        <a class="next" @click="next"><img :src="Chevronright"/></a>
            </div>
            <div>
                <div class="imageSlider">
                    <transition-group name="fade" tag="div">
                        <div class="imageSlider-wrapper" v-for="number in [currentNumber]" v-bind:key="number" @mouseover="stopRotation" @mouseout="startRotation">
                            <span class="white-text">{{ currentContent.title}}</span>
                            <p class="white-text">{{ currentContent.desc}}</p>
                            <b-button class="carousel-button" variant="outline-light">Selengkapnya</b-button>
                        </div>
                    </transition-group>
                    <ol class="carousel-indicators">
                        <li v-for="(content, index) in CarAct" :key="index" @click="goToSlide(index)" :class="{active: index === currentNumber}">
                            <span></span>
                        </li>
                    </ol>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import ImageBibit from '~/assets/assets/image/activity.png'
import Chevronright from '~/assets/assets/icon/chevron-right.svg'
import Chevronleft from '~/assets/assets/icon/chevron-left.svg'

export default {
    data(){
        return {
            ImageBibit,Chevronright,Chevronleft,
            CarAct: [
                {
                    title: "Bibit Unggul - Pengembangan Bakat Talenta Muda Indonesia",
                    desc: "Sebagai salah satu bentuk implementasi visi GMEDIA dengan menerapkan CSV (Corporate Shared Value), GMEDIA membangun sebuah program bibit unggul yang fokus pada pengembangan minat dan bakat talenta muda yang dibimbing sejak dini untuk menjadi talenta unggul muda. Pada program ini kami fokus dalam bidang Teknologi Informasi, olahraga dan seni budaya. Talenta muda yang ikut dalam program ini akan didampingi oleh para profesional di bidangnya masing-masing.",
                },
                {
                    title: "Bibit Unggul - Pengembangan Bakat Talenta Muda Indonesia",
                    desc: "Sebagai salah satu bentuk implementasi visi GMEDIA dengan menerapkan CSV (Corporate Shared Value), GMEDIA membangun sebuah program bibit unggul yang fokus pada pengembangan minat dan bakat talenta muda yang dibimbing sejak dini untuk menjadi talenta unggul muda. Pada program ini kami fokus dalam bidang Teknologi Informasi, olahraga dan seni budaya. Talenta muda yang ikut dalam program ini akan didampingi oleh para profesional di bidangnya masing-masing.",
                },
                {
                    title: "Bibit Unggul - Pengembangan Bakat Talenta Muda Indonesia",
                    desc: "Sebagai salah satu bentuk implementasi visi GMEDIA dengan menerapkan CSV (Corporate Shared Value), GMEDIA membangun sebuah program bibit unggul yang fokus pada pengembangan minat dan bakat talenta muda yang dibimbing sejak dini untuk menjadi talenta unggul muda. Pada program ini kami fokus dalam bidang Teknologi Informasi, olahraga dan seni budaya. Talenta muda yang ikut dalam program ini akan didampingi oleh para profesional di bidangnya masing-masing.",
                },
                {
                    title: "Bibit Unggul - Pengembangan Bakat Talenta Muda Indonesia",
                    desc: "Sebagai salah satu bentuk implementasi visi GMEDIA dengan menerapkan CSV (Corporate Shared Value), GMEDIA membangun sebuah program bibit unggul yang fokus pada pengembangan minat dan bakat talenta muda yang dibimbing sejak dini untuk menjadi talenta unggul muda. Pada program ini kami fokus dalam bidang Teknologi Informasi, olahraga dan seni budaya. Talenta muda yang ikut dalam program ini akan didampingi oleh para profesional di bidangnya masing-masing.",
                },
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
            if(this.currentNumber == this.CarAct.length - 1){
                this.currentNumber = 0;
            } else {
                this.currentNumber++;
            }
        },
        prev() {
            if(this.currentNumber <= 0) {
				this.currentNumber = this.CarAct.length - 1;
			} else {
				this.currentNumber -= 1
			}
        },
        goToSlide(index) {
            this.currentNumber = index;
        }
    },
    computed: {
        currentContent(){
            return this.CarAct[Math.abs(this.currentNumber) % this.CarAct.length];
        },
    },
}
</script>s  
<style scoped>

.white-text{
    color:white;
}

#content3{
    margin: 20px 0 20px 0;
    display: flex;
    flex-direction: column;
    align-items: center;
}
.content-titles{
    display: flex;
    align-items: center;
    flex-direction: column;
    gap: 10px;
    margin: 15px 0 15px 0;
}

.content-titles > span{
    width: max-content;
}

.content-title{
    font-size: 45px;
    font-weight: 700;
    line-height: 41px;
    letter-spacing: 0.25px;
    text-align: center;
}

.content-title-desc{
    font-size: 29px;
    font-weight: 400;
    line-height: 28px;
    letter-spacing: 0.15000000596046448px;
    text-align: center;
    letter-spacing: 0.15px;
    color: #8a8a8a;
}

.content-card{
    height: 35.677vw;
    /* height: min-content; */
    width: 83.021vw;
    margin: 1.042vw 0 1.042vw 0;
    border-radius: 8px;
    position: relative;
    overflow: hidden;
    background: linear-gradient(to left, rgba(0, 0, 0, 0.253) 0%, rgb(0, 0, 0) 100%);
}

.content-card > img{
    width: 100%;
    height: 100%;
    object-fit: cover;
    position: absolute;
    top: 0;
    left: 0;
    z-index: -100;
    opacity: 0.7;
}

.carousel-button{
    font-size: 18px;
    width: 150px;
    height: 57px;
    border-radius: 8px;
    border: 1px solid #fff;
    color: #fff;
}

.carousel-button:hover{
    color: #000;
}

.timer {
  position: absolute;
  bottom: -100px;
}

.imageSlider {
  position: absolute;
  display: flex;
  width: 50%;
  height: 100%;
  justify-items: flex-start;

}

.imageSlider-nav {
  position: absolute;
  bottom: 0;
  right: 0;
  display: flex;
  border-radius: 10px 0 0 0;
  overflow: hidden;
  z-index: 9;
}

.imageSlider-nav .next,
.imageSlider-nav .prev {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 60px;
  height: 60px;
  background: #02539E;
  opacity: 0.6; 
  color: #4DB6AC;
  cursor: pointer;
}

.imageSlider-nav .next:hover,
.imageSlider-nav .prev:hover {
  background-color: rgba(255, 255, 255, 0.8);
}

.imageSlider-nav .prev {
  margin-right: 1px;
}

.imageSlider .imageSlider-wrapper {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  padding: 2.604vw;
  display: flex;
  flex-direction: column;
  gap: 1.563vw;
  height: 100%;
}

.imageSlider-wrapper span{    
    font-size: 1.667vw;
    font-weight: 700;
    line-height: 1.667vw;
    letter-spacing: 0em;
    text-align: left;
}

.imageSlider-wrapper p {
    font-size: 1.094vw;
    font-weight: 400;
    line-height: 1.979vw;
    letter-spacing: 0.5px;
    text-align: left;
}

.imageSlider .imageSlider-item {
  position: relative;
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: 50% 50%;
}

.imageSlider-nav a img{
    width: 50%;
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

.carousel-indicators{
    gap: 24px;
    margin: 0 0 20px 3.5vw;
    justify-content: flex-start;
}

.carousel-indicators li{
    width: 78px;
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
  width: 78px;
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

@media screen and (max-width: 1079px) {
    .imageSlider {
        width: 50%;
        /* height: min-content; */
    }

    .imageSlider-wrapper{
        height: max-content;
    }

    .imageSlider-wrapper span{
        font-size: 20px;
        line-height: 20px;
    }

    .imageSlider-wrapper p{
        font-size: 12px;
        text-align: justify;
    }    
    .carousel-button{
        font-size: 14px;
        width: 120px;
        height: 40px;
    }

    .carousel-indicators{
        margin: 0 0 5px 3.5vw;
    }
    
    .carousel-indicators li{
        width: 30px;
    }

    .active span {
        width: 30px;
    }
}

@media screen and (max-width: 944px) {
    .imageSlider {
        width: 70%;
    }

    .imageSlider-wrapper span{
        font-size: 20px;
        line-height: 20px;
        text-align: center;
    }

    .imageSlider-wrapper p{
        font-size: 14px;
        line-height: 15px;
        text-align: justify;
    }
    .content-card{
        height: 350px;
    }    
}

@media screen and (max-width: 711px) {
    .imageSlider {
        width: 100%;
    }
    
    .content-title{
        font-size: 24px;
        font-weight: 700;
        line-height: 41px;
        letter-spacing: 0.25px;
        text-align: center;
    }

    .content-title-desc{
        font-size: 18px;
    }
    .content-card{
        height: 350px;
    }
}

</style>