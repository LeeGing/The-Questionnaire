<template>
  <div id="app">
    <img src="./assets/logo.png">
    <router-view></router-view>
    <h1> Welcome to Questions </h1>
    <button v-on:click="add">ADD</button>
    <button v-on:click="sub">SUB</button>
    <p> {{axelateral}} </p>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      axelateral: 0
    }
  },
  methods: {
    greet: function (greeting) {
      alert(greeting)
      window.location = 'http://www.youtube.com'
    },
    add: function () {
      this.axelateral += 1
    },
    sub: function () {
      this.axelateral -= 1
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
 