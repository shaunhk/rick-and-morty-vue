<template lang="html">
  <div id="">
    <episode-list :episodes="episodes" :selected-episode="selected-episode"></episode-list>
  </div>
</template>

<script>
import EpisodeList from '@/components/EpisodeList.vue'
export default {
  name: 'selected-episodes',
  props: ["selected-episode"],
  components: {
    "episodeList": EpisodeList
  }
}
</script>

<style lang="css" scoped>
</style>
