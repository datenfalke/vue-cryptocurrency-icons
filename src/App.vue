<template>
  <div id="app">
    <IconCrypto coinname="ETH" color="color" format="svg"/>
  </div>
</template>

<script>
import IconCrypto from './components/IconCrypto.vue'

export default {
  name: 'app',
  components: {
    IconCrypto
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
