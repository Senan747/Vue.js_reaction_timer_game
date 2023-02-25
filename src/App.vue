<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isplaying" >Play</button>
  <Blocks v-if="isplaying" :delay="delay" @end="endGame"/>
  <Results v-if="showResult" :score="score"/>
</template>

<script>
import Blocks from "./components/block.vue"
import Results from './components/results.vue'



export default {
  name: 'App',
  components: { Blocks, Results },
  data(){
    return{
      isplaying: false,
      delay: null,
      score: null,
      showResult: false
    }
  },

  methods: {
    start(){
      this.delay = 2000 + Math.random() * 5000
      this.isplaying = true
      this.showResult = false
      this.score = null
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isplaying = false
      this.showResult = true
      console.log(this.score)
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button{
  padding:10px 20px;
  border:none;
  background: #0f8364;
  color:white;
  font-size:17px;
  border-radius:5px;
  user-select: none;
}
p{
  user-select:none;
}
</style>
