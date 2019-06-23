<template lang="html">
  <div id="app">
    <h1>Enter the multiverse!</h1>
    <episode-list :episodes="episodes"></episode-list>
    <episode-detail :episodeLads="episodeLads"></episode-detail>

    <!-- <img src="./assets/multiverse.jpg"> -->
  <!-- <div id="character-list" v-for="character in this.episodeLads">
    <img :src="character.image" id="image">
    {{character.name}}
  </div> -->
  </div>
</template>

<script>

import { eventBus } from '@/main.js'
import EpisodeList from './components/EpisodeList.vue'
import EpisodeDetail from './components/EpisodeDetail.vue'

export default {
  name: 'app',
  components: {
    "episode-list": EpisodeList,
    "episode-detail": EpisodeDetail
  },
  data(){
    return {
      peopleLinks: [],
      episodes: [],
      episodeLads: [],
      ladsPromises: [],
      selectedEpisode: null
    }
  },
  mounted() {
    // this.getallCharacters()
    this.getallEpisodes(),
    eventBus.$on('episode-selected', (selectedEpisode) => {
      this.selectedEpisode = selectedEpisode,
      this.getallCharacters()
    })
  },
  methods: {
    getallEpisodes(){
      const promises = [1, 2].map(num =>
      {return fetch(`https://rickandmortyapi.com/api/episode?page=${num}`)
      .then(res => res.json())})
      Promise.all(promises)
      .then(data => data.map(obj => {return obj.results}))
      .then(data => this.episodes = data.reduce((flat, toFlatten) => flat.concat(toFlatten), []))
    },
    getallCharacters(){
    //   const promises = this.companies.map(symbol => {
    // return
    if(this.selectedEpisode){
    fetch(`${this.selectedEpisode.url}`)
    .then(response => response.json())
  // })
  //
  // Promise.all(promises)
  .then(data =>  this.peopleLinks = data.characters)
  .then(() => this.sum())}},
  sum(){this.ladsPromises = this.peopleLinks.map(person => {
    return fetch(`${person}`)
    .then(collect => collect.json())})
  Promise.all(this.ladsPromises)
  .then(data => this.episodeLads = data)
}
}
}
</script>

<style>

li {
  list-style-type: none;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#logo {
  width: 20px;
  height: 20px;
}

#list {
  text-align: left;
}

</style>
