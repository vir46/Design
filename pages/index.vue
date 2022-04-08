<template>
  <div>
    <Navbar class="navbar-component"/>
    <Body/>
    <Footer/>
  </div>
</template>

<script>
import Navbar from '~/components/Navbar.vue'
import Body from '~/components/Body.vue'
import Footer from '~/components/Footer.vue'
export default {
  name: 'IndexPage',
  components: {
    Navbar,
    Body,
    Footer
  }
}
</script>

<style>
*{
  scroll-behavior: smooth;
}

.navbar-component{
  position: sticky;
  top: 0;
  z-index: 999;
}
</style>