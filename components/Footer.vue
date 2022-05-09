<template>
  <div id="footer">
      <div class="link-container">
              <div class="link-content" v-for="(link, index) in links" v-bind:key="index">
                  <span class="link-title">{{ link.name }}</span>
                  <div class="link-link"> 
                      <a v-for="(ct, index) in link.content" 
                      :key="index"
                      href="#" >
                       {{ ct.name }}
                       </a>
                  </div>
              </div>
      </div>
      <Footerone/>
      <div class="content-copyright">
          <span>© 2022 PT Media Sarana Data. All rights reserved.</span>
      </div>
  </div>
</template>

<script>
import Footerone from '~/components/foot-comp/footer1.vue'

export default {
    components: {
        Footerone,
    },
    data(){
        return{
            links: [
               {
                   name: "Produk",
                   content: [
                       {name: "Internet Solution"},
                       {name: "Application Development"},
                       {name: "Ultimate Data Center"},
                       {name: "Network Integration"},
                       {name: "Manage Service & IT Consultant"},
                   ]
               },
               {
                   name: "Solusi",
                   content: [
                       {name: "Education"},
                       {name: "Government"},
                       {name: "Corporate"},
                       {name: "Hospitality"},
                       {name: "Food & Beverages"},
                   ]
               },
               {
                   name: "Perusahaan",
                   content: [
                       {name: "Tentang"},
                       {name: "Kontak"},
                       {name: "Partner"},
                       {name: "Karir"},
                   ]
               },
               {
                   name: "Informasi",
                   content: [
                       {name: "Event"},
                       {name: "Artikel"},
                       {name: "Press Release"},
                   ]
               },
               {
                   name: "Support",
                   content: [
                       {name: "Network Tools"},
                       {name: "Subscribe Method"},
                       {name: "Looking Glass"},
                   ]
               }
           ] 
        }
    }
}
</script>

<style scoped>
div#footer{
    height: max-content;
    background: #F5F5F5;
    margin: 20px 0 0 0;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    align-items: center;
}
.link-container{
    display: flex;
    justify-content: center;
    width:  83.622vw;
    padding-top: 50px;
    flex-direction: row;
    justify-content: space-between;
}

.link-title{
    font-size: 16px;
    font-weight: 700;
    line-height: 20px;
    letter-spacing: 0.15000000596046448px;
    text-align: left;
}

.link-content{
    display: flex;
    flex-direction: column;
    gap: 14px;
}

.link-link > a{
    color: black;
}

.link-link{
    display: flex;
    flex-direction: column;
}


.content-copyright{
    background: #F0F0F0;
    height: 44px;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
}

.content-copyright > span{
    font-size: 14px;
    font-weight: 400;
    line-height: 24px;
    letter-spacing: 0.25px;
    text-align: center;
}

@media screen and (max-width: 999px) {
    .link-container{
        width:  83.622vw;
        flex-wrap: wrap;
        flex-direction: row;
        justify-content: space-between;
        gap: 80px;
    }
}
</style>