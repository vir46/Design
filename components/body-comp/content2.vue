<template>
    <div id="contenttwo">
        <div class="content-container">
            <div>
                <div class="content-menu">
                    <div class="content-menu-item" v-for="(content, index) in contents2" v-bind:key="'C'+ index"
                    :class="{ selected: content.select}" 
                    @click="toggleSelect(index)">
                        <div>
                            <span class="content-title">{{content.title}}</span>
                            <span class="content-desc">{{content.desc}}</span>
                        </div>
                    </div>
                </div>
               <div class="content-collage-image">
                    <div class="content-image-container" v-for="(collage, index) in collages" v-bind:key="index">
                        <img class="content-image" :src="collage.url"/>
                        <span class="content-caption">{{collage.caption}}</span>
                    </div>
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
                { title: "Connecting Peoples Everyday", desc: "Bikin aktifitas selalu seru dan lebih produktif", select: false},
                { title: "Upgrade Digital Enterprise", desc: "Memfasilitasi kebutuhan digital industri", select:false},
                { title: "Technology for Humanity", desc: "Membawa masa depan teknologi lebih humanis", select: false},
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
    height:  max-content;
    padding: 3.646vw 0 3.646vw 0;
    background-color: #f5f5f5;
    display: flex;
    align-items: center;
    justify-content: center;
}

.content-container > div{
    width: 83.056vw;
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    flex-direction: row;
}
.content-menu{
    height: 36.875vw    ;
    display: flex;
    flex-direction: column;
    gap: 30px;
}

.content-menu-item{
    display: flex;
    flex-direction: row;
    width: 100%;
    align-items: center;
    cursor: pointer;
}


.content-menu-item > div{
    display: flex;
    width: 100%;
    flex-direction: column;
    justify-content: center;
    color: #1f1f1f;
}


.selected > div > span:first-child{
    color: #02539E;
}

.selected::before{
    content: ".";
    width: 0.208vw;
    height: 2.604vw;
    border-radius: 2px;
    background-color: #02539E;
}


.content-title{
    font-size: 1.667vw;
    font-weight: 700;
    width: max-content;
}

.content-desc{
    font-size: 1.094vw;
    font-weight: 400;
    letter-spacing: 0.5px;
    width: max-content;
}

.content-collage-image{
    width: 50vw;
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
    width: 25vw;
    height: 18.4375vw;
    opacity: 0.8;
}

.content-caption{
    position: absolute;
    font-weight: 700;
    font-size: 1.354vw;
    color: #ffffff;
    margin-bottom: 15px;
}

.selected > div{
    background-color: #EFEFEF;
    padding: 0.260vw 2.083vw 0.260vw 0.781vw;
    border-radius: 8px;
    width:  30.781vw;
}

@media screen and (max-width: 776px) {
    .content-container > div{
        align-items: center;
        justify-content: space-between;
        flex-direction: column;
    }
    .content-collage-image{
        width: 60.055vw;
    }
    .content-image{
        position: relative;
        width: 30vw;
        height: 22.626vw;
        opacity: 0.8;
    }
    .content-menu-item > div{
        width: 317px;
        align-items: flex-start;
    }
    .content-menu{
        width: 70%;
        height: max-content;
    }
    .content-container > div{
        gap: 20px;
    }
    .content-container{
        height: max-content;
        padding: 20px 0 20px 0;
    }
    .content-title{
        font-size: 17px;
    }
    .content-desc{
        font-size: 11px;
    }
    .selected > div{
        padding: 0.260vw 2.083vw 0.260vw 0.781vw;
        width:  100%;
    }    
    .selected::before{
        width: 2px;
        height: 30px;
        border-radius: 2px;
        background-color: #02539E;
    }
}
    @media screen and (max-width: 400px){
        .content-collage-image{
            width: 240px;
        }
        .content-image{
            width: 119.7px;
            height: 90.27774px;
        }        
        .content-caption{
            font-size: 5.402px;
        }
    }
</style>