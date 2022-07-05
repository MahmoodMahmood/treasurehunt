<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <br>
    <h2> Question #1: Xibu cbcb't kpc jt </h2>

    <form @submit.prevent>
      <input @submit.prevent="checkGuess" v-model="userGuess" type="text" placeholder="Enter guess">
      <button @click="checkGuess">Check Guess</button>
    </form>
    <p class="wrongGuess">You guess incorrectly</p>
    <div class="hintbox">
      <button @click="showHint(1)"> Show hint #1 </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      userGuess: '',
    }
  },
  methods: {
    checkGuess() {
      if (this.userGuess.toLowerCase() === 'hello') {
        alert('You guessed correctly!')
      } else {
        alert('You guessed incorrectly!')
      }
    },
    showHint(hintNumber) {
      if (hintNumber === 1) {
        alert('The answer is hello')
      }
    }
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
