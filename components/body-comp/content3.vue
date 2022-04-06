<template>
    <div id="content3">
        <div class="content-titles">
            <span class="content-title">Aktifitas Sarat Manfaat</span>
            <span class="content-title-desc">Potret beragam aktifitas sarat manfaat</span>
        </div>
        <div class="content-card">
            <img :src="ImageBibit" class="content-card-background"/>
            <div>
                <b-carousel
                    id="carousel-no-animation"
                    fade
                    indicators
                >
                    <div class="carousel-inner" v-for="(car, index) in CarAct" v-bind:key="index">
                        <div class="carousel-item" :class="{ 'active' : index === 0 }">
                            <div class="carousel-caption">
                                <span>{{ car.title }}</span>
                                <p>{{ car.desc }}</p>
                                <b-button class="carousel-button" variant="outline-light">Selengkapnya</b-button>
                            </div>
                        </div>
                    </div>
                </b-carousel>
            </div>
        </div>
    </div>
</template>

<script>
import ImageBibit from '~/assets/assets/image/activity.png'
export default {
    data(){
        return {
            ImageBibit,
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
                    title: "Lorem more,,, Same lorem, nothing different",
                    desc: "Sebagai salah satu bentuk implementasi visi GMEDIA dengan menerapkan CSV (Corporate Shared Value), GMEDIA membangun sebuah program bibit unggul yang fokus pada pengembangan minat dan bakat talenta muda yang dibimbing sejak dini untuk menjadi talenta unggul muda. Pada program ini kami fokus dalam bidang Teknologi Informasi, olahraga dan seni budaya. Talenta muda yang ikut dalam program ini akan didampingi oleh para profesional di bidangnya masing-masing.",
                },
            ]
        }
    },
}
</script>s  
<style scoped>

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

.carousel-item{
    width:  80%;
    height: 514px;
}

.carousel-caption{
    display: flex;
    flex-direction: column;
    justify-content: center;
    width: 100%;
    height: 100%;
    gap: 27px;
    /* overflow: scroll; */
}

.carousel-caption > span{
    font-size: 24px;
    font-weight: 700;
    line-height: 32px;
    letter-spacing: 0em;
    text-align: left;
}

.carousel-caption > p{
    font-size: 16px;
    font-weight: 400;
    line-height: 28px;
    letter-spacing: 0.5px;
    text-align: left;
}

.carousel-button{
    width: 30%;
    margin: 10px 0 10px 0;
}
#carousel-no-animation{
    width: 50%;
}
</style>