<template>
  <div>
      <div id="Navbar" >
        <div class="navbar-logo">
          <img :src="Logo" alt="GMedia Logo">
        </div>
        <div class="navbar-content">
          <div class="content-link">
            <span v-for="(link, index) in content" :key="index" @click="turnOnDropdown(index)">{{link.text}}<img :class="{'reverse': index == indexDropdown && isDropdown == true}"
             :src="Chevrondown"/></span>
          </div>
          <div class="language-switch">
            <div class="language-choose" 
            v-for="(lang, index) in language" :key="index"
            :class="{'langchoose': lang.active == true}"
            @click="changeLanguage(index)"
            >
            {{lang.text}}
            </div>
          </div>
          <div class="button-login">
            <a href="#">Login</a>
          </div>
        </div>
      </div>
      <div id="SubNavbar" v-if="isDropdown">
        <div class="sub-title">{{ this.content[indexDropdown].text }}</div>
        <div  class="sub-content">
          <span v-for="(content, index) in content[this.indexDropdown].dropdown" :key="index">
            <a href="#">
              {{content.text}}
            </a>
          </span>
        </div>
      </div>
  </div>
</template>

<script>
import Logo from '~/assets/assets/logo.png';
import Chevrondown from '~/assets/assets/icon/chevron-down.svg';

export default {
  name: 'Navigation',
  data() {
    return {
      Logo,Chevrondown,
      content: [
        { text: 'Produk', dropdown: [{ text: 'Produk 1' }, { text: 'Produk 2' }] },
        { text: 'Solusi', dropdown: [{ text: 'Solusi 1' }, { text: 'Solusi 2' }] },
        { text: 'Perusahaan', dropdown: [{ text: 'Perusahaan 1' }, { text: 'Perusahaan 2' }] },
        { text: 'Informasi', dropdown: [{ text: 'Informasi 1' }, { text: 'Informasi 2' }] },
      ],
      language: [
        { text: 'ID', active: true, },
        { text: 'EN', active: false, },
      ],
      indexDropdown: 0,
      isDropdown: false,
    }
  },
  methods: {
    turnOnDropdown(index) {
      if(this.isDropdown == false){
        this.isDropdown = true;
        this.indexDropdown = index;
      }else{
        if(this.indexDropdown == index){
          this.isDropdown = false;
          this.indexDropdown = 0;
        }else{
          this.indexDropdown = index;
        }
      }
    },
    changeLanguage(index) {
      this.language.forEach(lang => {
        lang.active = false;
      });
      this.language[index].active = true;
    },
  },
}
</script>

<style scoped>

.reverse{
  transform: rotate(180deg);
}

#SubNavbar {
  position: absolute;
  width: 100%;
  height: 84px;
  background-color: #e9e9e9;
  display: flex;
  align-items: center;
  flex-direction: column;
  gap: 10px;
  border-bottom: #02539E solid 2px;
}

.sub-title{
  margin-top: 10px;
  font-weight: bold;
  width: 60%;
  border-radius: 15px;
  height: 20px;
  background: white;
  display: flex;
  align-items: center;
  justify-content: center;
}

.sub-content{
  width: 60%;
  display: flex;
  flex-wrap: wrap;
  gap: 3vw;
}

.sub-content span a{
  color: black;
}
#Navbar{
  width: 100%;
  height: 84px;
  background-color: #fff;
  overflow: hidden;
  display: flex;
  align-items: center;
  /* box-shadow: 0px 1px 1px rgba(0,0,0,0.1); */
}

.navbar-logo{
  display:flex;
  width: 50%;
  justify-content: center;
  align-items: center;
}

.navbar-logo img{
  width: 112px;
  height: 36px;
}

.navbar-content{
  display: flex;
  width: 47%;
  justify-content: flex-end;
  align-items: center;
  gap: 1vw;
  
}

.content-link{
  display: flex;
  gap: 4vw;
  margin-right: 2vw;
  cursor: pointer;
  user-select: none;
}

.content-link img{
  margin-left: 0.5vw;
}

.language-choose{
  background: white;
  color: black;
  padding: 2px;
  width: 45px;
  display: flex;
  justify-content: center;
}

.language-switch{
  display: flex;
  flex-direction: row;
  border-radius: 15px;
  overflow: hidden;
  border: 1px solid #EBEBEB;
}

.langchoose{
  background: #02539E !important;
  color: white !important;
}


/*  Button CSS */

.button-login a{
  background-color: transparent;
  border-color: #ffc107;
  color: #ffc107;
  font-size: 14px;
  border: solid 1px;
  padding: 8px 15px 8px 15px;
  border-radius: 10px;
  cursor: pointer;
}

.button-login a:hover{
  background-color: #ffc107;
  color: #fff;
  text-decoration: none;
}

label.language-label{
  margin: 0;
}
</style>