<template>
  <div class="hello">
    <h1 class="page-title centered">CRYPTO CURRENCY WITH VUE JS</h1>
    <hr style="padding-bottom: 30px;">
    <div id="crypto-container" v-for="(value, key) in cryptos">
      <span class="left">{{ key }}</span>
      <span class="right">${{  value.USD }}</span>

    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',
  data: () => ({
    cryptos: [],
    errors: []
  }),

  created () {
    axios.get('https://min-api.cryptocompare.com/data/pricemulti?fsyms=BTC,ETH,IOT&tsyms=USD')
    .then(response => {
      this.cryptos = response.data
      console.log(response)
    })
    .catch(e => {
      this.errors.push(e)
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
body{
  background: #f1f1f1;
}

div#crypto-container {
  background:white;
  width: 70%;
  margin: 0 auto 4px auto;
  padding: 1em;
  box-shadow: 1px 1px 0 lightgray;
}

span.left {
  font-weight: bold;
}
span.right {
  float: right;
}
.centered{
  text-align: center;
  color: green;
}
</style>
