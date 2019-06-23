<template lang="html">
  <div id="app">
  <div id="character-list" v-for="character in this.episodeLads">
    <img :src="character.image" id="image">
    {{character.name}}
  </div>
  </div>
</template>

<script>

export default {
  name: 'app',
  components: {

  },
  data(){
    return {
      companyProfiles: null,
      people: [],
      episodeLads: [],
      ladsPromises: []
    }
  },
  mounted() {
    this.getallCharacters()
  },
  methods: {
    getallCharacters(){
    //   const promises = this.companies.map(symbol => {
    // return
    fetch(`https://rickandmortyapi.com/api/episode/1`)
    .then(response => response.json())
  // })
  //
  // Promise.all(promises)
  .then(data =>  this.people = data.characters)
  .then(() => this.sum())},
  sum(){this.ladsPromises = this.people.map(person => {
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
