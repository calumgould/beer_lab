<template>
  <div id="app">
    <h1>Roosap's Beer Emporium</h1>
    <div class="main-container">
      <beer-detail :beer="selectedBeer"></beer-detail>
      <div class="list">
        <div class="left-list">
          <beers-list :beers="beers"></beers-list>
        </div>
        <div class="right-list">
          <favs-list :favBeers="favBeers"></favs-list>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import {eventBus} from './main.js'
import BeersList from './components/BeersList.vue'
import BeerDetail from './components/BeerDetail.vue'
import FavsList from './components/FavsList.vue'
export default {

  name: 'App',
  data(){
    return {
      beers: [],
      favBeers: [],
      selectedBeer: null
    }
  },
  components: {
    'beers-list': BeersList,
    'favs-list': FavsList,
    'beer-detail': BeerDetail
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(data => this.beers = data)

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer
    })
    eventBus.$on('fav-beer-selected', (beer) => {
      this.favBeers.push(beer)
    })
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

.main-container {
  display: flex;
  justify-content: space-between;
  width: 80%;
  margin: 0 auto;
}

h1 {
  font-size: 5em;
  padding-bottom: 0.5em;
}

.list {
  width: 100%;
  display: flex;
}

.left-list, .right-list {
  width: 50%;
  text-align: center;
}
</style>
