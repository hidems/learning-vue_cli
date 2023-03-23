<template>
  <div>
    <myheader></myheader>
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <GeoNames></GeoNames>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import myheader from './components/myheader'
import GeoNames from './components/GeoNames'

export default {
  components: {
    myheader,
    GeoNames,
    HelloWorld,
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
