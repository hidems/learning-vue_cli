<template>
  <div>
    <myheader></myheader>
    <p v-if="msg.length > 0">
      {{ msg }}
    </p>
    <p v-else>
      No Text
    </p>
    <input type="text" v-model="msg">
    <button @click="clear()">clear</button>
    <button @click="created()">call</button>
  </div>

  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
// export default {
//   name: 'App',
//   components: {
//     HelloWorld
//   }
// }
import myheader from './components/myheader'

export default {
  components: {
    myheader
  },
  data () {
    return {
      msg: 'Hello World'
    }
  },
  methods: {
    clear () {
      this.msg = ''
    }
  },
  created () {
    fetch('http://www.geonames.org/postalCodeLookupJSON?postalcode=10504&country=US')
    .then( response => {
      return response.json()
    })
    .then( json => {
      this.msg = json.postalcodes[0].adminName1
    })
    .catch( (err) => {
      this.msg = err // エラー処理
    });
  }
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
