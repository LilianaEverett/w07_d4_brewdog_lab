<template lang="html">
  <div id="detailWrapper">

    <div v-if="beer">
      <ul class="detailData">
        <li class="name">Name: {{ beer.name }}</li>
        <li>ABV: {{ beer.abv }}</li>
        <li>Description: {{beer.description}}</li>

        <beer-fav :beer="beer"></beer-fav>

      </ul>
      </div>

      <div>
        <img :src="beer.image_url" :alt="beer.name">
      </div>

  </div>
</template>

<script>
import AddToFavouritesButton from './AddToFavouritesButton.vue'
import { eventBus } from '../main.js'

export default {
  name: "beer-detail",
  props: ['beer'],
  components: {
    "beer-fav": AddToFavouritesButton
  }


}
</script>

<style lang="css" scoped>
img {
  padding-right: 40px;
  padding-left: 40px;
  padding-top: 20px;
  height: 300px;
}
#detailWrapper {
  display: flex;
  flex-direction: row;
  box-sizing: border-box;
  background: #cbc8b9;
  padding: 10px;
  height: 400px;
  margin-top: 30px;
}

.name {
  font-size: 24px;
}

ul{
  list-style-type: none;
}
</style>
