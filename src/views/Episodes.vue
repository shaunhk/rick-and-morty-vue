<template lang="html">
  <div id="episode-list">
    <episode-list :episodes="episodes" :selected-episode="selected-episode"></episode-list>
  <episode-detail :episodeLads="episodeLads"></episode-detail>
</div>
</template>

<script>

import EpisodeList from '@/components/EpisodeList.vue'
import EpisodeDetail from './components/EpisodeDetail.vue'

export default {
  name: 'episode',
  props: ["episodes", "selected-episode"],
  components: {
    "episode-list": EpisodeList,
    "episode-detail": EpisodeDetail
  }
}
</script>

<style lang="css" scoped>
</style>
