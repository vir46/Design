<template>
  <div>
      <hr class="borderline">
      <div class="content-upper">
          <div>
              <div>
              <img  class="content-upper-logo" :src="Logo"/>
          </div>
          <div class="content-upper-contact">
              <span class="content-upper-title">Kontak</span>
              <span><img :src="Contact" />081234567890</span>
              <span><img :src="Mail" />email@dimensicloud.com</span>
          </div>
          <div class="content-upper-find">
                <span  class="content-upper-title">Temukan Kami</span>
                <div class="social-media">
                    <a href="#"><img :src="Instagram"/></a>
                    <a href="#"><img :src="Youtube"/></a>
                    <a href="#"><img :src="Facebook"/></a>
                    <a href="#"><img :src="Twitter"/></a>
                </div>
          </div>
          </div>
      </div>
      <hr class="borderline">
      <div class="content-town" >
          <div class="content-town-text" v-for="(town, index) in towns" :key="index">
                {{town.name}}
                <div v-if="index < towns.length - 1">.</div>
          </div>
      </div>
  </div>
</template>

<script>
import Logo from "~/assets/assets/logo.png"
import Youtube from "~/assets/assets/social-media/youtube.svg"
import Instagram from "~/assets/assets/social-media/instagram.svg"
import Facebook from "~/assets/assets/social-media/facebook.svg"
import Twitter from "~/assets/assets/social-media/twitter.svg"
import Contact from "~/assets/assets/icon/contact.svg"
import Mail from "~/assets/assets/icon/mail.svg"


export default {
    data(){
        return{
            Logo,Youtube,Instagram,Facebook,Twitter,Contact,Mail,
            towns: [
                { name: "Yogyakarta"},
                { name: "Semarang"},
                { name: "Solo"},
                { name: "Salatiga"},
                { name: "Mataram"},
                { name: "Jakarta"},
                { name: "Bali"},
                { name: "Surayabaya"},
                { name: "Purwokerto"},
            ]
        }
    },
}
</script>

<style scoped>

.borderline{
    border: 1px solid #EBEBEB;
    width: 80%;
}
.content-upper{
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    align-items: center;
    height: 150px;
    width:  1594.6752px;
}

.content-upper > div{
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    width: 70%;
}
.content-upper-logo{
    width: 9.1vw;
}

.content-upper-contact{
    display: flex;
    flex-direction: column;
    height: 100px;
    gap: 10px;
}

.content-upper-contact img{
    margin-right: 0.4vw;
}
.content-upper-find{
    height: 100px;
    gap: 5px;
}

.content-upper-title{
    font-size: 16px;
    font-weight: 700;
    line-height: 20px;
    letter-spacing: 0.15px;
    text-align: left;
    color: #616161;
}

.content-town{
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    height: 20px;
    gap: 1vw;
    margin-bottom: 15px;
}
.content-town-text{
    display: flex;
    flex-direction: row;
    justify-content: center;
    gap: 1vw;
}

.social-media{
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    align-items: center;
    gap: 0.6vw;
}
</style>