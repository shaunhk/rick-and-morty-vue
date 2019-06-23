<template lang="html">
  <ul>
    <episode-list-item v-for="(episode, index) in episodes" :episode="episode" :key="index"></episode-list-item>
  </ul>
</template>

<script>
import EpisodeListItem from './EpisodeListItem.vue'
export default {
  name: 'episode-list',
  props: ['episodes'],
  components: {
    "episode-list-item": EpisodeListItem
  }
}
</script>

<style lang="css" scoped>
</style>
