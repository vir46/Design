<template>
    <div id="content3">
        <div class="content-titles">
            <span class="content-title">Aktifitas Sarat Manfaat</span>
            <span class="content-title-desc">Potret beragam aktifitas sarat manfaat</span>
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
                        <li v-for="(content, index) in CarAct" :key="index" @click="goToSlide(index)" :class="{active: index === currentNumber}"></li>
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
                    title: "Lorem Ipsum - is a dummy text for testing",
                    desc: "Sebagai salah satu bentuk implementasi visi GMEDIA dengan menerapkan CSV (Corporate Shared Value), GMEDIA membangun sebuah program bibit unggul yang fokus pada pengembangan minat dan bakat talenta muda yang dibimbing sejak dini untuk menjadi talenta unggul muda. Pada program ini kami fokus dalam bidang Teknologi Informasi, olahraga dan seni budaya. Talenta muda yang ikut dalam program ini akan didampingi oleh para profesional di bidangnya masing-masing.",
                },
                {
                    title: "Lorem more,,, Same lorem, nothing different,, writed for the carousel test",
                    desc: "Sebagai salah satu bentuk implementasi visi GMEDIA dengan menerapkan CSV (Corporate Shared Value), GMEDIA membangun sebuah program bibit unggul yang fokus pada pengembangan minat dan bakat talenta muda yang dibimbing sejak dini untuk menjadi talenta unggul muda. Pada program ini kami fokus dalam bidang Teknologi Informasi, olahraga dan seni budaya. Talenta muda yang ikut dalam program ini akan didampingi oleh para profesional di bidangnya masing-masing.",
                },
                {
                    title: "The Last Part of Carousel",
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
}

.content-titles > span{
    width: max-content;
}

.content-title{
    font-size: 34px;
    font-weight: 700;
    line-height: 41px;
    letter-spacing: 0.25px;
    text-align: center;
}

.content-title-desc{
    font-size: 20px;
    font-weight: 400;
    line-height: 28px;
    letter-spacing: 0.15000000596046448px;
    text-align: center;
}

.content-card{
    height: 514px;
    width: 1196px;
    margin: 20px 0 20px 0;
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
    width: max-content;
    margin: 0 0 10px 0;
}


.timer {
  position: absolute;
  bottom: -100px;
}

.imageSlider {
  position: absolute;
  display: flex;
  /* padding: 50px; */
  width: 50%;
  height: 100%;
  justify-items: flex-start;

}

.imageSlider-nav {
  position: absolute;
  bottom: 0;
  right: 0;
  display: flex;
  border-radius: 10px 10px 0 0;
  overflow: hidden;
  z-index: 9;
}

.imageSlider-nav .next,
.imageSlider-nav .prev {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 90px;
  height: 90px;
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
  padding: 50px 0 0 50px;
  display: flex;
  flex-direction: column;
  gap: 30px;
  height: 100%;
}

.imageSlider-wrapper span{    
    font-size: 24px;
    font-weight: 700;
    line-height: 32px;
    letter-spacing: 0em;
    text-align: left;
}

.imageSlider-wrapper p {
    font-size: 16px;
    font-weight: 400;
    line-height: 28px;
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
    width: 3.125vw;
}

</style>