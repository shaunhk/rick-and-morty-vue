<template lang="html">
  <li v-on:click="handleClick">{{episode.episode}}: {{episode.name}}</li>
</template>

<script>
import { eventBus } from '../main.js'
export default {
  name: 'episode-list-item',
  props: ['episode'],
  methods: {
    handleClick(){
      eventBus.$emit('episode-selected', this.episode)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
