<template>
  <div id="content4">
      <hr class="dashed">
      <div class="content-maintitles">
          <span class="content-maintitle">Terupdate di G-Outlook</span>
          <span class="content-subtitle">Menarik dan siap memperkaya pengetahuan Kamu</span>
      </div>
      <div class="content-head">
          <img :src="PicArt1" class="content-head-image"/>
          <div class="content-info">
              <span class="content-title">Memahami Pentingnya Peran Data Center Pasca Peristiwa Kebakaran</span>
              <span class="content-date">Sel, 21 Des 2021</span>
              <span class="content-desc">Tanggal 2 Desember 2021 lalu, beberapa layanan internet serta beberapa situs dan aplikasi sempat lumpuh selama beberapa saat.
                    Menurut Rhevin Fardhika Putra, data center atau pusat data adalah sebuah bangunan yang digunakan untuk menyimpan banyak server. 
                    Salah satu fungsinya adalah untuk menampung traffic website atau aplikasi web. Agar traffic website atau aplikasi web lancar, 
                    pastinya pemilik website harus memilih data center...</span>
          </div>
      </div>
      <div class="content-under">
          <div class="content-container">
                <b-card
                    v-for="(content, index) in contents" v-bind:key="index"
                    :title="content.headtitle"
                    class="b-card"
                    v-bind:img-src="content.image"
                    style="max-width: 20vw; height: 392px;"
                >
                    <span class="content-date">{{content.date}}</span>
                    <b-card-text class="content-desc">
                    {{content.caption}}
                    </b-card-text>
                </b-card>
          </div>
          <b-button class="content-button" variant="outline-primary">
              <div><span>Lihat lainnya</span></div>
              <div class="content-button-img"><img :src="Arrow" /></div>
            </b-button>
      </div>
  </div>
</template>

<script>
import PicArt1 from '~/assets/assets/image/article-1.png'
import PicArt2 from '~/assets/assets/image/article-2.png'
import PicArt3 from '~/assets/assets/image/article-3.png'
import PicArt4 from '~/assets/assets/image/article-4.png'
import Arrow from '~/assets/assets/icon/arrow-right.svg'

export default {
    data() {
        return {
        PicArt1,PicArt2,PicArt3,PicArt4,Arrow, 
        contents: [
            { image: PicArt2, headtitle: "9+ Tips Belajar Coding Terlengkap untuk Pemula" , date: "Sel, 21 Des 2020", caption: "Inilah yang pasti Anda bingungkan saat mau mempelajari coding dasar. Dunia..." },
            { image: PicArt3, headtitle: "10+ Cara Cek Website Down atau Tidak dengan Mudah..." , date: "Sel, 21 Des 2021", caption: "Anda pasti pernah mengunjungi sebuah website, tapi website tersebut tidak..." },
            { image: PicArt4, headtitle: "Corporate Shared Value", date: "Sel, 21 Des 2021", caption: "Coorporate Shared Value adalah bentuk bisnis yang mengedepankan nilai dan kebermanfaatan dalam..." },
        ],
        }
    }
}
</script>

<style scoped>
#content4{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
.content-maintitles{
    display: flex;
    align-items: center;
    flex-direction: column;

}

.content-maintitle{
    font-size: 34px;
    font-weight: 700;
    line-height: 41px;
    letter-spacing: 0.25px;
    text-align: center;
}

.content-subtitle{
    font-size: 20px;
    font-weight: 400;
    line-height: 28px;
    letter-spacing: 0.15000000596046448px;
    text-align: center;
}

hr.dashed {
  border: 1px solid #EBEBEB;
  opacity: 0.5;
  width: 60%;
}

.content-head-image{
    width: 31.313vw;
    height: 100%;
}

.content-head{
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    border-radius: 8px;
    width: 62.292vw;
    gap: 2vw;
    margin: 20px 0 20px 0;
    box-shadow: 4px 4px 8px 0px #02539E0F;
}

.b-card{
    box-shadow: 4px 4px 8px 0px #02539E0F;
}

.content-title{
    font-size: 20px;
    font-weight: 600;
    line-height: 24px;
    letter-spacing: 0em;
    text-align: left;
}

.content-date{
    font-size: 16px;
    font-weight: 400;
    line-height: 20px;
    letter-spacing: 0.15000000596046448px;
    text-align: left;
}

.content-desc{
    font-size: 16px;
    font-weight: 400;
    line-height: 28px;
    letter-spacing: 0.5px;
    text-align: justify;
}

.content-info{
    display: flex;
    align-items: left;
    flex-direction: column;
    width: 29.896vw;
    gap: 10px;
    padding: 20px;
}

.content-under{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;

}

.content-container{
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    gap: 0.9vw;
}

.content-button{
    margin: 30px 0 30px 0;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
}

.content-button img{
    filter: invert(1);
}

.content-button div{
    display: flex;
    width: 50%;
    justify-content: flex-end;
}

</style>