<template>
  <div id="app">
    <img src="./assets/logo.png">
    <router-view></router-view>
    <h1> Welcome to Questions </h1>
    <button v-on:click="add">ADD</button>
    <button v-on:click="sub">SUB</button>
    <p v-if="displaynumber === 5"> {{displaynumber}} </p>
    <p v-if="displaynumber === 3"> {{displaynumber}} </p>
    <p v-if="displaynumber === 0"> {{displaynumber}} </p>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      displaynumber: 0
    }
  },
  methods: {
    greet: function (greeting) {
      alert(greeting)
      window.location = 'http://www.youtube.com'
    },
    add: function () {
      this.displaynumber += 1
    },
    sub: function () {
      this.displaynumber -= 1
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
 