<template>
  <img alt="Vue logo" src="./assets/eid-mubarak.svg" class="hello-image">
  <HelloWorld msg="Aboodi! Welcome to your Eid treasure hunt!"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
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
.hello-image {
  width: 80%;
  max-width: 300px;
}
</style>
