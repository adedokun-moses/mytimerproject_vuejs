<template>
  <h1>Moses Reaction Timer</h1>
  <button class="btn" @click="start"  :disabled="isPlaying" >Play</button>

  <FirstBlock v-if="isPlaying" :delay="delay" @end="endGame" />
<!--   <p v-if="showResults">reactionTime {{score}} ms </p> -->
   <Results v-if="showResults" :score ="score" />
</template>

<script>
  import FirstBlock from './components/block_mode.vue'
   import Results  from './components/result_block.vue'

  export default {
      name: 'App',
      components: { FirstBlock, Results },

      data(){
        return{
          isPlaying: false,
          delay: null,
          score: null, 
          showResults: false
        }
      },

      methods:{
        start(){
            this.delay = 2000 + Math.random() * 5000
            this.isPlaying = true 
            this.showResults = false
           // console.log(this.delay)
        },

        endGame(reactionTime){
          this.score = reactionTime
          this.isPlaying = false
          this.showResults = true
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

.btn{
  padding: 20px;
  /* background: green; */
  color: red;
  border-radius: 10px;
  outline: none;
  border: none;
  width: 40%;
}
</style> 
