<template lang="html">
  <div>
    <h1>BrewDog Beers</h1>

    <data class="main-container"></data>
    <fav-list :favBeers="favBeers"></fav-list>
    <beer-dropdown :beers="beers"></beer-dropdown>
    <beer-detail :beer="selectedBeer"></beer-detail>
  </div>
</template>

<script>

import BeersDropDown from './components/BeersDropDown.vue'
import BeerDetail from './components/BeerDetail.vue'
import FavList from './components/FavList.vue'

import { eventBus } from './main.js'

export default {
  data(){
    return {
      beers: [],
      selectedBeer: null,
      favBeers: []
    }
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(beers => this.beers = beers)

    eventBus.$on('fav-list', (beer) => {
      this.favBeers.push(beer)
    })

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer
    })
  },
  components: {
    "beer-dropdown": BeersDropDown,
    "beer-detail": BeerDetail,
    "fav-list": FavList

  }
}
</script>

<style lang="css" scoped>
div {
  font-family: arial;
  margin-left: 20px;
  margin-right: 20px;
}

h1 {
  font-family: arial;
  text-align: center;
  color: #333;
}
.main-container {
  font-family: arial;
  display: flex;
  justify-content: space-between;
  width: 80%;
  margin: 0 auto;
}


</style>
