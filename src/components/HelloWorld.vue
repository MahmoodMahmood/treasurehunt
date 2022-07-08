<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Welcome to your Eid treasure hunt</h2>
    <br>
    <h2> Your challenge is to decode the following message: <strong> Rwtrz pqdkt iwt ugxsvt </strong> </h2>
    <br>
    <div class="container-sm">
      <form @submit.prevent class="input-group mb-3">
        <input @submit.prevent="checkGuess" v-model="userGuess" type="text" placeholder="Enter decoded message"
          class="form-control">
        <button @click="checkGuess" class="btn btn-outline-secondary">Check Guess</button>
      </form>
    </div>
    <br>
    <template v-for="n in 3" v-bind:key="n.id">
      <button @click="showHint(n)" :disabled="current_time < n * 60" class="btn btn-primary"> Show hint #{{ n }}
      </button>
    </template>
    <div id="hintContainer" class="container">
      <img v-if="hintToShow > -1" :src="getHintImagePath()" alt="hint" class="figure-img img-fluid rounded w-25 p-3">
      <figcaption class="figure-caption"> {{getHintCaption()}} </figcaption>
    </div>
  </div>
  <br>
</template>

<script>
const HINTS_IMAGE = ["julius-caesar.jpg", "cypher.webp", "age-of-empires.jpg"]
const HINTS_CAPTION = ["This guy's title", "His last name", "You just need the first word of this one."]
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
      if (this.userGuess.toLowerCase() === 'check above the fridge') {
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
        return require('../assets/' + HINTS_IMAGE[this.hintToShow - 1])
      }
    },
    getHintCaption() {
      if (this.hintToShow > -1) {
        return HINTS_CAPTION[this.hintToShow]
      }
    }
  },
  beforeUnmount() {
    // prevent memory leak
    clearInterval(this.interval)
  },
  created() {
    this.loaded_time = new Date()
    // update the time every second
    this.interval = setInterval(() => {
      const cur_time = new Date()
      this.current_time = Math.floor((cur_time - this.loaded_time) / 1000)
    }, 1000)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
