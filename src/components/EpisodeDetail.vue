<template lang="html">
  <div v-if="episodeLads" id="episode-detail">
    <div>
      Character List
    </div>
    <div v-for="lad in episodeLads">
        <!-- <canvas id="tutorial" width="150" height="150"></canvas> -->
        <img :src="lad.image" :alt="lad.name">
        <h3>{{lad.name}}</h3>
        <p>Species: {{lad.species}}</p>
        <p>Home World: {{lad.location.name}}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'episode-detail',
  props: ['episodeLads'],
  // methods: {
  //   draw() {
  //     let canvas = document.getElementById('tutorial');
  //     if (canvas.getContext) {
  //       let ctx = canvas.getContext('2d');
  //     }
  //   }
  // }
}
</script>

<style lang="css" scoped>
  canvas { border: 1px solid black; }
</style>
