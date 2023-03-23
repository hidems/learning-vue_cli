// Do not work now, Nov 2022
<template>
  <div>
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
</template>

<script>
export default {
  name: 'GeoNames',
  data () {
    return {
      msg: 'Hello World'
    }
  },
  methods: {
    clear () {
      this.msg = ''
    },
    created() {
      console.log('created');
      fetch('http://www.geonames.org/postalCodeLookupJSON?postalcode=10504&country=US', {
        method: 'GET',
        headers: {
          'Content-Type': 'application/json',
          'Access-Control-Allow-Origin': '*',
          'Access-Control-Allow-Headers': 'Origin, X-Requested-With, Content-Type, Accept',
          'Access-Control-Allow-Methods': 'GET, POST, PUT, DELETE, OPTIONS'
        },
      })
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
  },
}

</script>