<template>
    <div id="contentone">
        <div v-for="(content, index) in contents" v-bind:key="index" class="content-all">
            <div class="content-container" v-if="content.queue == 'normal'">
                <img class="content-image" :src="content.imageurl"/>
                <div class="content-text">
                    <span class="content-title">{{content.title}}</span>
                    <span class="content-desc">{{content.desc}}</span>
                    <b-button class="content-button" variant="outline-primary">Selengkapnya</b-button>
                </div>
            </div>
            <div class="content-container" v-else>
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
  width: 76%;
}

.content-all{
    display: flex;
    justify-content: center;
}

.content-container{
    margin: 50px 40px 100px 40px;
    display: flex;
    width:  1594.6752px;
    align-items: center;
    justify-content: space-between;
}

.content-image{
    border-radius: 8px;
    width: 762px;
    height: 457px;
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
    font-size: 21px;
}

.content-title{
    font-weight: 700;
    font-size: 32px;
}

.content-button{
    font-size: 18px;
    width: 170px;
    height: 63px;
    border-radius: 8px;
    border: 1px solid #02539E;
    color: #02539E;
    padding: 10px;
    letter-spacing: 1.25px;
}
.content-button:hover{
    color: white;
}
</style>