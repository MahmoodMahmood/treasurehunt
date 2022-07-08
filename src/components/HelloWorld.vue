<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <br>
<h2> Answer the following question: Rwtrz pqdkt iwt ugxsvt </h2>

    <form @submit.prevent>
      <input @submit.prevent="checkGuess" v-model="userGuess" type="text" placeholder="Enter guess">
      <button @click="checkGuess">Check Guess</button>
    </form>
    <p class="wrongGuess">You guess incorrectly</p>
    <template v-for="n in 3" v-bind:key="n.id">
      <button @click="showHint(n)" :disabled="current_time < n*60"> Show hint #{{ n }} </button>
    </template>
    <div id="hintContainer">
      <img v-if="hintToShow > -1" :src="getHintImagePath()" alt="hint">
    </div>
  </div>
</template>

<script>
const HINTS = ["julius-caesar.jpg", "cypher.webp", "age-of-empires.jpg"]
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      userGuess: '',
      hintToShow: -1,
      loaded_time: null,
      interval: null,
      current_time: null
    }
  },
  methods: {
    checkGuess() {
      if (this.userGuess.toLowerCase() === 'above the fridge') {
        alert('You guessed correctly!')
      } else {
        alert('You guessed incorrectly!')
      }
    },
    showHint(hintNumber) {
      this.hintToShow = hintNumber
    },
    getHintImagePath() {
      if (this.hintToShow > -1) {
        return require('../assets/' + HINTS[this.hintToShow - 1])
      }
    }
  },
  beforeUnmount(){
    // prevent memory leak
    clearInterval(this.interval)
  },
  created() {
    this.loaded_time = new Date()
    // update the time every second
    this.interval = setInterval(() => {
      const cur_time = new Date()
      this.current_time = Math.floor((cur_time - this.loaded_time)/1000)
    }, 1000)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
