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
          <div class="switch">
            <input id="language-toggle" class="check-toggle check-toggle-round-flat" type="checkbox">
            <label class="language-label" for="language-toggle"></label>
            <span class="on">ID</span>
            <span class="off">EN</span>
          </div>
          <div class="button-login">
            <a href="#">Login</a>
          </div>
        </div>
      </div>
      <div id="SubNavbar" v-if="isDropdown"
      data-aos="zoom-in"
      data-aos-duration="300">
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
import AOS from 'aos';
import 'aos/dist/aos.css';

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
  },
  mounted() {
    AOS.init();
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
  box-shadow: 0px 1px 1px rgba(0,0,0,0.1);
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

/* Switch CSS */

.switch {
  position: relative;
  display: inline-block;
  margin: 0 5px 0 0;
}

.switch > span {
  position: absolute;
  top: 10px;
  pointer-events: none;
  font-family: 'Helvetica', Arial, sans-serif;
  font-weight: bold;
  font-size: 12px;
  text-transform: uppercase;
  text-shadow: 0 1px 0 rgba(0, 0, 0, .06);
  width: 50%;
  text-align: center;
}

input.check-toggle-round-flat:checked ~ .off {
  color: #02539E;
}

input.check-toggle-round-flat:checked ~ .on {
  color: #fff;
}

.switch > span.on {
  left: 0;
  padding-left: 2px;
  color: #02539E;
}

.switch > span.off {
  right: 0;
  padding-right: 4px;
  color: #fff;
}

.check-toggle {
  position: absolute;
  margin-left: -9999px;
  visibility: hidden;
}
.check-toggle + label {
  display: block;
  position: relative;
  cursor: pointer;
  outline: none;
  -webkit-user-select: none;
  user-select: none;
}

input.check-toggle-round-flat + label {
  padding: 2px;
  width: 97px;
  height: 35px;
  background-color: #02539E;
  -webkit-border-radius: 60px;
  border-radius: 60px;
}
input.check-toggle-round-flat + label:before, input.check-toggle-round-flat + label:after {
  display: block;
  position: absolute;
  content: "";
}

input.check-toggle-round-flat + label:before {
  top: 2px;
  left: 2px;
  bottom: 2px;
  right: 2px;
  background-color: #02539E;
  -webkit-border-radius: 60px;
  border-radius: 60px;
}
input.check-toggle-round-flat + label:after {
  top: 4px;
  left: 4px;
  bottom: 4px;
  width: 48px;
  background-color: #fff;
  -webkit-border-radius: 52px;
  border-radius: 52px;
  -webkit-transition: margin 0.2s;
  transition: margin 0.2s;
}

input.check-toggle-round-flat:checked + label:after {
  margin-left: 44px;
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