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
                    class="b-card"
                    v-bind:img-src="content.image"
                    
                >
                    <span class="card-title">{{content.headtitle}}</span>
                    <span class="content-date">{{content.date}}</span>
                    <b-card-text class="content-desc">
                    {{content.caption}}
                    </b-card-text>
                </b-card>
          </div>
          <b-button class="content-button" variant="outline-primary">
              <div><span>Lihat lainnya</span></div>
              <div class="arrow-logo"></div>
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
            { image: PicArt2, headtitle: "9+ Tips Belajar Coding Terlengkap untuk Pemula" , date: "Sel, 21 Des 2021 ", caption: "Inilah yang pasti Anda bingungkan saat mau mempelajari coding dasar. Dunia..." },
            { image: PicArt3, headtitle: "10+ Cara Cek Website Down atau Tidak dengan Mudah..." , date: "Sel, 21 Des 2021", caption: "Anda pasti pernah mengunjungi sebuah website, tapi website tersebut tidak..." },
            { image: PicArt4, headtitle: "Coorporate Shared Value", date: "Sel, 21 Des 2021", caption: "Coorporate Shared Value adalah bentuk bisnis yang mengedepankan nilai dan kebermanfaatan dalam..." },
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
    gap: 15px;
    margin: 15px 0 15px 0;
}

.content-maintitle{
    font-size: 45px;
    font-weight: 700;
    line-height: 41px;
    letter-spacing: 0.25px;
    text-align: center;
}

.content-subtitle{
    font-size: 29px;
    font-weight: 400;
    line-height: 28px;
    letter-spacing: 0.15000000596046448px;
    text-align: center;
    color: #8a8a8a;
    letter-spacing: 0.15px;
}

hr.dashed {
  border: 1px solid #EBEBEB;
  opacity: 0.5;
  width: 82%;
}

.content-head-image{
    width: 43.111vw;
    height: 100%;
}

.content-head{
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    overflow: hidden;
    border-radius: 8px;
    width: 83.056vw;
    margin: 20px 0 20px 0;
    box-shadow: 4px 4px 8px 0px #02539E0F;
}

.b-card{
    box-shadow: 4px 4px 8px 0px #02539E0F;font-weight: 600;
    width: 27vw; 
    height: max-content;
}

.card-body{
    display: flex;
    flex-direction: column;
    gap: 1vw;
    min-height: 222px;
}

.content-title{
    font-size: 1.529vw;
    font-weight: 600;
    line-height: 1.412vw;
    text-align: left;
}

.content-date{
    font-size: 1.235vw;
    font-weight: 400;
    line-height: 1vw;
    text-align: left;
    color: #616161;
}

.content-desc{
    font-size: 1.235vw;
    font-weight: 400;
    line-height: 2.176vw;
    text-align: justify;
}

.content-info{
    display: flex;
    align-items: flex-start;
    flex-direction: column;
    width: 38.094vw;
    gap: 0.882vw;
    height: 100%;
    padding: 0 20px 0 20px;
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
    justify-content: space-between;
    width: 83.021vw;
}

.content-button{
    margin: 30px 0 30px 0;
    width: 100%;
    height: 49px;
    display: flex;
    justify-content: center;
    align-items: center;
    border: 1px solid #02539E;
    color: #02539E;
}

.content-button:hover .arrow-logo{
    background-color: white;
}

.content-button:hover{
    color: white;
}

.content-button div{
    display: flex;
    width: 50%;
    letter-spacing: 1.25px;
    justify-content: flex-end;
}

.card-title{
    font-size: 1.235vw;
    font-weight: 600;
    line-height: 1.412vw;
    text-align: left;
    color: black;
}

.arrow-logo{
    background-color: #02539E;
    mask: url('~/assets/assets/icon/arrow-right.svg') no-repeat right;
    width: 1px;
    height: 14px;
    justify-items: flex-end;
}

@media screen and (max-width: 699px) {    
    .content-head-image{
        width: 100%;
    }

    .content-head{
        flex-direction: column;
    }
        
    .content-title{
        font-size: 3.058vw;
        line-height: 2.824vw;
    }

    .content-date{
        font-size: 2.470vw;
        line-height: 2vw;
    }

    .content-desc{
        font-size: 2.470vw;
        line-height: 4.352vw;
    }

    .content-info{
        width: 100%;
        gap: 1.882vw;
        height: max-content;
        padding: 2.5vw;
    }
    .content-container{
        gap: 20px;
        flex-direction: column;
    }

    .b-card{
        width: 100%; 
        max-height: max-content;
    }

    
    .b-card .card-body{
        height: max-content;
    }

    
    .card-title{
        font-size: 2.470vw;
        line-height: 2.824vw;
    }
    .content-maintitle{
        font-size: 24px;
    }

    .content-subtitle{
        font-size: 18px;
    }

}
</style>