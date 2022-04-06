<template>
    <div id="Navbar">
        <b-navbar toggleable="sm" type="light" variant="light">
            <b-navbar-brand href="#">
            <img :src="Logo" alt="GMedia Logo" height="36px" class="d-inline-block align-text-top">
            </b-navbar-brand>

            <b-navbar-nav class="ml-auto">
                <b-nav-item-dropdown text="Produk" right>
                    <b-dropdown-item href="#">Example 1</b-dropdown-item>
                    <b-dropdown-item href="#">Example 2</b-dropdown-item>
                </b-nav-item-dropdown>
                <b-nav-item-dropdown text="Solusi" right>
                    <b-dropdown-item href="#">Example 1</b-dropdown-item>
                    <b-dropdown-item href="#">Example 2</b-dropdown-item>
                </b-nav-item-dropdown>
                <b-nav-item-dropdown text="Perusahaan" right>
                    <b-dropdown-item href="#">Example 1</b-dropdown-item>
                    <b-dropdown-item href="#">Example 2</b-dropdown-item>
                </b-nav-item-dropdown>
                <b-nav-item-dropdown text="Informasi" right>
                    <b-dropdown-item href="#">Example 1</b-dropdown-item>
                    <b-dropdown-item href="#">Example 2</b-dropdown-item>
                </b-nav-item-dropdown>
                <div class="switch">
                    <input id="language-toggle" class="check-toggle check-toggle-round-flat" type="checkbox">
                    <label for="language-toggle"></label>
                    <span class="on">ID</span>
                    <span class="off">EN</span>
                </div>
                <b-button class="button-login" variant="outline-warning">Login</b-button>
            </b-navbar-nav>
        </b-navbar>
    </div>
</template>

<script>
import Logo from '../assets/assets/logo.png';

export default {
  name: 'Navigation',
  data() {
    return {
      Logo,
    }
  }
    
}
</script>

<style scoped>
#Navbar{
  z-index: 1;
  position: relative;
}

.navbar-nav > li{
  padding-left:10px;
  padding-right:10px;
}

.switch {
  position: relative;
  display: inline-block;
  margin: 0 5px;
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

.button-login{
    height: 35px;
    margin-left:15px;
    margin-right:15px;
}

</style>