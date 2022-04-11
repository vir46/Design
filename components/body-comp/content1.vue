<template>
    <div id="contentone">
        <div 
        data-aos="fade-up"
        data-aos-duration="1500"
        v-for="(content, index) in contents" v-bind:key="index">
            <div class="content-container" v-if="content.queue == 'normal'">
                <img class="content-image" :src="content.imageurl"/>
                <div class="content-text">
                    <span class="content-title">{{content.title}}</span>
                    <span class="content-desc">{{content.desc}}</span>
                    <b-button class="content-button" variant="outline-primary">Selengkapnya</b-button>
                </div>
            </div>
            <div 
            data-aos="fade-up"
            data-aos-duration="1500"
            class="content-container" v-else>
                <div class="content-text">
                    <span class="content-title">{{content.title}}</span>
                    <span class="content-desc">{{content.desc}}</span>
                    <b-button class="content-button" variant="outline-primary">Selengkapnya</b-button>
                </div>
                <img class="content-image" :src="content.imageurl"/>
            </div>
            <div v-if="index < contents.length - 1">
                <hr class="dashed">
            </div>
        </div>
    </div>
</template>

<script>
import ImageIs from '~/assets/assets/image/internet-solution.png'
import ImageAd from '~/assets/assets/image/app-development.png'
import ImageDc from '~/assets/assets/image/data-center.png'
export default {
    data() {
        return {
            ImageIs, ImageAd, ImageDc,
            contents: [
                {
                    imageurl : ImageIs,
                    title: "Internet Solution",
                    desc: "Merupakan produk terbaik GMEDIA yang memberikan anda pengalaman berinternet dengan minimum latency",
                    queue: "normal",
                },
                {
                    imageurl : ImageAd,
                    title: "Application Development",
                    desc: "Membuatkan usaha anda aplikasi, yang dilengkapi dengan Internet of Things (IOT) sehingga membantu mengolah serta mengumpulkan data dan menyajikan data, dengan data yang memiliki kredibilitas dan keakuratan yang tinggi",
                    queue: "reverse",
                },
                {
                    imageurl : ImageDc,
                    title: "Ultimate Data Center",
                    desc: "Ultimate Data Center adalah salah satu produk unggulan, yang menjawab solusi penyimpanan data yang aman dan terkelola dengan sistem integrasi tebaik",
                    queue: "normal",
                },  
            ]
        }
    },
}
</script>

<style scoped>


hr.dashed {
  border: 1px solid #EBEBEB;
  opacity: 0.5;
  width: 60%;
}

.content-container{
    margin: 50px 40px 100px 40px;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 5vw;
}

.content-image{
    border-radius: 25px;
    width: 572px;
    height: 343px;
}

.content-text{
    gap: 20px;
    display: flex;
    flex-direction: column;
    align-items: left;
    justify-content: center;
}

.content-desc{
    text-align: justify;
    width: 572px;
    font-size: 16px;
}

.content-title{
    font-weight: 700;
    font-size: 24px;
}

.content-button{
    width: 150px;
}
</style>