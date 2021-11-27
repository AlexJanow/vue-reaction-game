<template>
<h1>How fast can you react?</h1>
<button @click="start" :disabled="isPlaying">Play</button>
<Block v-if="isPlaying" :delay="delay" @end="endGame" @abort="abortGame" />
<Results v-if="showResults" :score="score" />
<p v-show="aborted" > {{abortMessage}} </p>
</template>

<script>
import Block from "./components/Block.vue"
import Results from "./components/Results.vue"

export default {
  name: 'App',
  components: { Block, Results },
  data(){
      return {
        isPlaying: false,
        delay: null,
        score: null,
        showResults: false,
        aborted: false
      }   
  },
  methods: {
    start(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false
      this.aborted = false

    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
    },
    abortGame(msg) {
      this. abortMessage = msg
      this.isPlaying = false
      this.aborted = true
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
h1{
  color:white;
  font-weight: 1000;
  
  text-shadow: 2px 2px rgb(92, 92, 92);
}
p {
  color:white;
}
button {
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
  }
  button[disabled] {
    opacity: 0.2;
    cursor: not-allowed;
  }
  
</style>
