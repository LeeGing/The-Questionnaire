<template>
  <div id="app">
    <div>
      <router-view></router-view>
      <h1> Welcome to Questions </h1>
      <button v-on:click="add">ADD</button>
      <button v-on:click="sub">SUB</button>
      <p> Points: {{displaynumber}} </p>
      <button v-on:click="add">ADD</button>
      <button v-on:click="sub">SUB</button>
    </div>
    <div>
      <!-- Dynamic direction of questions would be nice. -->
      <!-- Static index would be easier. -->
      <p v-if="displaynumber === 0">I like being in an office.</p>
      <button v-on:click="add">True</button>
      <button v-on:click="sub">False</button>
      <p v-if="displaynumber > 2"> Sounds like you're going to love working as a receptionist! </p>
      <p v-if="displaynumber < 5"> - - - - - </p>
      <p v-if="displaynumber < 0"> You probably don't want to be a receptionist.</p>

    </div>
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
 