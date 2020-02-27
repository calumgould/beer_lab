<template>
  <div id="app">
    <h1>Beer List</h1>
    <beers-list :beers="beers"></beers-list>
  </div>
</template>

<script>

import BeersList from './components/BeersList.vue'
export default {

  name: 'App',
  data(){
    return {
      beers: []
    }
  },
  components: {
    'beers-list': BeersList
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
