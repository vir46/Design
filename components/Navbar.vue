<template>
  <div>
      <div id="Navbar" >
        <div class="navbar-logo">
          <img :src="Logo" alt="GMedia Logo">
        </div>
        <div class="navbar-content" v-if="widthscreen == 'normal'">
          <div class="content-link">
            <span 
              v-for="(link, index) in content" :key="index" 
              @click="turnOnDropdown(index)">
                {{link.text}}
                <img :class="{'reverse': index == indexDropdown && isDropdown == true}" :src="Chevrondown"/>
            </span>
          </div>
          <div class="language-switch">
            <div class="language-choose" 
              v-for="(lang, index) in language" :key="index"
              :class="{'langchoose': lang.active == true}"
              @click="changeLanguage(index)">
                {{lang.text}}
            </div>
          </div>
          <div class="button-login">
            <a href="#">Login</a>
          </div>
        </div>
        <div class="navbar-content" v-else>
          <Burger
            :isBurgerActive="isBurgerActive"
            @changestat="toggle()"
          />
        </div>
      </div>
      <Sidebar
        :isPanelOpen="isBurgerActive"
        @closeSidebarPanel="toggle()">
      <ul class="sidebar-panel-nav">
        <div class="sidebar-logo">
          <img :src="Logo" alt="GMedia Logo">
        </div>
        <li v-for="(link, index) in content" :key="index" >
          <span 
            @click="turnOnDropdown(index)">
              {{link.text}}
              <img :class="{'reverse': index == indexDropdown && isDropdown == true}" :src="Chevrondown"/>
          </span>
          <div v-if="index == indexDropdown && isDropdown == true" class="subsidebar">
            <span v-for="(content, index) in content[indexDropdown].dropdown" :key="index">
              <a href="#">{{content.text}}</a>
            </span>
          </div>
        </li>
        <div class="language-switch">
            <div class="language-choose" 
              v-for="(lang, index) in language" :key="index"
              :class="{'langchoose': lang.active == true}"
              @click="changeLanguage(index)">
                {{lang.text}}
            </div>
          </div>
          <div class="button-login">
            <a href="#">Login</a>
          </div>
      </ul>
    </Sidebar>
      <div id="SubNavbar" v-if="isDropdown && widthscreen == 'normal'">
        <div class="sub-title">{{ this.content[indexDropdown].text }}</div>
        <div  class="sub-content">
          <span v-for="(content, index) in content[this.indexDropdown].dropdown" :key="index">
              {{content.text}}
          </span>
        </div>
      </div>
  </div>
</template>

<script>
import Logo from '~/assets/assets/logo.png';
import Chevrondown from '~/assets/assets/icon/chevron-down.svg';
import Burger from '~/components/navbar-comp/burger.vue';
import Sidebar from '~/components/navbar-comp/sidebar.vue';

export default {
  name: 'Navigation',
  components: {
    Burger,
    Sidebar,
  },
  data() {
    return {
      Logo,Chevrondown,
      widthscreen: 'normal',
      isBurgerActive: false,
      content: [
        { text: 'Produk', dropdown: [{ text: 'Produk 1' }, { text: 'Produk 2' }] },
        { text: 'Solusi', dropdown: [{ text: 'Solusi 1' }, { text: 'Solusi 2' }] },
        { text: 'Perusahaan', dropdown: [{ text: 'Perusahaan 1' }, { text: 'Perusahaan 2' }] },
        { text: 'Informasi', dropdown: [{ text: 'Informasi 1' }, { text: 'Informasi 2' }] },
      ],
      language: [
        { text: 'ID', active: true, },
        { text: 'ENG', active: false, },
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
    toggle() {
      this.isBurgerActive = !this.isBurgerActive;
    },
    detectFirstScreen(){
      if(window.innerWidth < 1315){
        this.widthscreen = 'small';
      }else{
        this.widthscreen = 'normal';
      }
    }
  },
  mounted(){
    this.detectFirstScreen();
    window.addEventListener('resize', () => {
      if(window.innerWidth < 1315){
        this.widthscreen = 'small';
      }else{
        this.widthscreen = 'normal';
        this.isBurgerActive = false;
      }
    });
  },
}
</script>

<style scoped>

.reverse{
  transform: rotate(180deg);
}

ul {
    list-style-type: none;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    gap: 25px;
}

li span{
  user-select: none;
  cursor: pointer;
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

.subsidebar{
  display: flex;
  flex-direction: column;
  margin-left: 15px;
  font-weight: bold;
}

.subsidebar span a{
  color: black;
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

.sub-content span{
  color: black;
  user-select: none;
  cursor: pointer;
}

#Navbar{
  width: 100%;
  height: 84px;
  background-color: #fff;
  justify-content: center;
  overflow: hidden;
  display: flex;
  align-items: center;
}

.navbar-logo{
  display:flex;
  width: 41.528vw;
  justify-content: flex-start;
  align-items: center;
}

.sidebar-logo{
  display:flex;
  width: 60%;
  justify-content: center;
  align-items: center;
}

.sidebar-logo img{
  width: 112px;
  height: 36px;
  margin-bottom: 30px;
}

.navbar-logo img{
  width: 112px;
  height: 36px;
}

.navbar-content{
  display: flex;
  width: 41.528vw;
  height: max-content;
  justify-content: flex-end;
  align-items: center;
  flex-wrap: wrap-reverse;
  gap: 1vw;
  
}

.content-link{
  display: flex;
  gap: 1.5vw;
  cursor: pointer;
  user-select: none;
}

.content-link span{
  width: max-content;
  display: flex;
  gap: 5px;
  align-items: center;
}

.content-link > span > img{
  height: max-content;
}

.language-choose{
  cursor: pointer;
  background: white;
  font-size: 12px;
  color: black;
  width: 35px;
  height: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.language-switch{
  display: flex;
  width: max-content;
  flex-direction: row;
  border-radius: 8px;
  overflow: hidden;
  border: 1px solid #EBEBEB;
}

.langchoose{
  background: #02539E !important;
  color: white !important;
}

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

</style>