<template>
  <div>
    <Header />
    <SiderMenu />
    <router-view />
    <Footer />
  </div>
</template>

<script>
import Header from './Header';
import SiderMenu from './SiderMenu'
import Footer from './Footer'

export default {
  components: {
    Header,
    Footer,
    SiderMenu
  }
};
</script>

<style>

</style>