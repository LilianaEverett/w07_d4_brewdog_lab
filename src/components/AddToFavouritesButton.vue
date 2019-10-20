<template lang="html">
  <div>
    <button v-on:click="handleClick">Add to Fav's</button>

    <ul >
    </ul>
  </div>
</template>

<script>

import { eventBus } from '../main.js'

export default {
  name: 'beer-fav',

  props: ['beer'],
  methods: {
    handleClick(){
      eventBus.$emit('fav-list', this.beer)
    }
  }
}
</script>

<style lang="css" scoped>
button {
  background-color: dimgray;
  border: none;
  color: white;
  padding: 10px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 20px 2px;
  cursor: pointer;
  border-radius: 4px;
}
</style>
