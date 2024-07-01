<template>
  <div>
    <h1>Raction Timer Game</h1>
      <div @click="launchBlock" ref="name" class="play" :class="{'active':isPlaying}" >Start</div>
      <Block :delay="delay" v-if="isPlaying" @end="endGame"/>
      <Results v-if="showResults" :score="score"></Results>
 </div>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'
export default {
  name: 'App',
  components: {
    Block,
    Results
  },
  data(){
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
      isActive: false
    }
  },
  methods: {
    launchBlock(){
      this.delay = 2000 + Math.floor(Math.random() * 5000)
      this.isPlaying = true
      this.showResults = false
      this.isActive = true
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
      this.isActive = false
    }
  }
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
.play {
  background: #7fc88d;
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 10px 20px;
  cursor: pointer;
  display: inline-block;
  margin-top: 20px;
}
.play.active {
  background: #415345;
  color: #fff;
  cursor: not-allowed;
}

</style>
