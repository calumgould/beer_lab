<template>
  <div id="app">
    <h1>cheeky</h1>
  </div>
</template>

<script>


export default {
  name: 'App',
  data(){
    return {
      beers: []
    }
  },
  components: {

  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(data => this.beers = data)
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
