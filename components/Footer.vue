<template>
  <div id="footer">
      <div class="link-container">
          <div v-for="(link, index) in links" v-bind:key="index">
              <div class="link-content">
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
      </div>
      <Footerone/>
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
}
.link-container{
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: space-around;
    padding-top: 50px;
    flex-direction: row;
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
</style>