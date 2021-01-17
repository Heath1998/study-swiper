<template>
  <div id="app">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <swiper />
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import swiper from './components/swiper.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld,
    swiper
  }
}
</script>

<style>
body{
  margin: 0;
  padding: 0;
}
#app {
  width: 100%;
  height: 100vh;
  margin: 0;
  padding: 0;
  background: linear-gradient(148.24deg,#040404 -3.54%,#2f3133 101.2%);
}
</style>
