<template>
    <div id="contenttwo">
        <div class="content-container">
            <div class="content-menu"
            >
                <div class="content-menu-item" v-for="(content, index) in contents2" v-bind:key="'C'+ index"
                :class="{ selected: content.select}" 
                @click="toggleSelect(index)"
                >
                    <div>
                        <span class="content-title">{{content.title}}</span>
                        <span class="content-desc">{{content.desc}}</span>
                    </div>
                </div>
            </div>
            <div class="content-collage-image"
            >
                <div class="content-image-container" v-for="(collage, index) in collages" v-bind:key="index">
                    <img class="content-image" :src="collage.url"/>
                    <span class="content-caption">{{collage.caption}}</span>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Rumah from '~/assets/assets/image/internet-rumah.png'
import Sekolah from '~/assets/assets/image/internet-sekolah.png'
import Kantor from '~/assets/assets/image/internet-kantor.png'
import Hospitality from '~/assets/assets/image/internet-hospitality.png'

export default {
    name: 'Contenttwo',
    data() {
        return {
            Rumah,Sekolah,Kantor,Hospitality,
            contents2: [
                { title: "Connecting People Everyday", desc: "Bikin aktifitas selalu seru dan lebih produktif", select: false},
                { title: "Upgrade Digital Enterprise", desc: "Memfasilitasi kebutuhan digital industri", select:false},
                { title: "Technology For Humanity", desc: "Membawa masa depan teknologi lebih humanis", select: false},
                { title: "Teleporting Happiness", desc: "Berbagi kebahagian lintas jarak dan waktu", select: false},
            ],
            collages: [
                { url: Rumah, caption: "Internet untuk Rumah"},
                { url: Kantor, caption: "Internet untuk Kantor"},
                { url: Hospitality, caption: "Internet untuk Cafe, Hotel, dll"},
                { url: Sekolah, caption: "Internet untuk Sekolah"},
            ],
        }
    },
    methods: {
        toggleSelect(index) {
            this.contents2.forEach(content => {
                content.select = false
            })
            this.contents2[index].select = true;
        }
    },
    mounted: function() {
        this.toggleSelect(0);
    }
}
</script>

<style scoped>
.content-container{
    height: 660px;
    background-color: #f5f5f5;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    gap: 10vw;
}
.content-menu{
    height: 532px;
    display: flex;
    flex-direction: column;
    gap: 30px;
}

.content-menu-item{
    display: flex;
    flex-direction: row;
    cursor: pointer;
}


.content-menu-item > div{
    display: flex;
    width: 27vw;
    flex-direction: column;
    justify-content: center;
    color: #1f1f1f;
}

.content-title{
    font-size: 24px;
    font-weight: 700;
    width: max-content;
}

.content-desc{
    font-size: 16px;
    font-weight: 400;
    width: max-content;
}

.content-collage-image{
    width: 720px;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    border-radius: 8px;
    overflow: hidden;
    height: min-content;
}

.content-image-container{
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    align-items: center;
    background: linear-gradient(180deg, #1F1F1F 0%, #1F1F1F 100%);
}

.content-collage-container{
    width: min-content;
}

.content-image{
    position: relative;
    width: 360px;
    height: 266px;
    opacity: 0.6;
}

.content-caption{
    position: absolute;
    font-weight: 700;
    font-size: 20px;
    color: #ffffff;
    margin-bottom: 15px;
}
/* div first child */
.selected > div{
    background-color: #EFEFEF;
}

.selected > div > span:first-child{
    color: #02539E;
}

.selected::before{
    content: "";
    width: 5px;
    height: 60px;
    background-color: #02539E;
    position: relative;
    margin-right: 0.2vw;
}

/* .hovered{

} */
</style>