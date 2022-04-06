<template>
  <div>
    <Navbar/>
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
</style>