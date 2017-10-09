<template>
  <div id="app">
    <h1> ℒife-𝐴nswers.org</h1>  

<!-- Lumberjack Button -->
    <button v-on:click='lumberjack'>Lumberjack Questions</button>
    <div v-if="lumberjacknumber % 2 === 0">
      <img src="http://static.tvtropes.org/pmwiki/pub/images/lumberjack_5919.jpg" height="250px">
<!-- Lumberjack Questions -->
        <p v-if="questionnumber < 6"> Question: {{questionnumber}} </p>
        <p v-if="questionnumber === 1">Question 1: Do you like being outdoors.</p>
        <p v-if="questionnumber === 2">Question 2: Do you like to swing axes at trees? </p>
        <p v-if="questionnumber === 3">Question 3: Do you think you can fight a bear? </p>
        <p v-if="questionnumber === 4">Question 4: Do you make your own sandwiches? </p>
        <p v-if="questionnumber === 5">Question 5: Are you a big beared white sir? </p>
<!-- Lumberjack Answers -->
        <button v-if="questionnumber <= 5"v-on:click="add">Yes</button>
        <button v-if="questionnumber <= 5"v-on:click="sub">No</button>
<!-- Lumberjack Comments -->
        <p v-if="displaynumber === 5" class="comment"> Sounds like you're going to love working as a lumberjack! </p>
        <p v-if="displaynumber === 4" class="comment"> You may enjoy lumberjacking. </p>
        <p v-if="displaynumber === 3" class="comment"> You may enjoy lumberjacking. </p>
        <p v-if="displaynumber === 2" class="comment"> We may be on to something. </p>
        <p v-if="displaynumber === 1" class="comment"> We may be on to something. </p>
        <p v-if="displaynumber < 0" class="comment"> You probably don't want to be a lumberjack.</p>
        <p> Points: {{displaynumber}} </p>
      </div>

<!-- Element Bender Questions -->
    <button v-on:click='bender'>Bender Questions</button>
    <div v-if="bendernumber % 2 === 0">
<!-- Element Bender Questions -->
      <img src="https://i.pinimg.com/originals/48/3a/b0/483ab0cec0963d9f13e7675febb9e873.jpg" height="200px">
      <p v-if="questionnumber < 6"> Question: {{questionnumber}} </p>
      <div v-if="questionnumber === 1">
        <p>Question 1: Which element are you most comfortable with?</p>
        <button v-on:click="AFunc">Fire</button>
        <button v-on:click="BFunc">Water</button>
        <button v-on:click="CFunc">Air</button>
        <button v-on:click="DFunc">Earth</button>
      </div>
      <div v-if="questionnumber === 2">
        <p>Question 2: What is your favorite color? </p>
        <button v-on:click="AFunc">Red</button>
        <button v-on:click="BFunc">Blue</button>
        <button v-on:click="CFunc">Gray</button>
        <button v-on:click="DFunc">Brown</button>
      </div>
      <div v-if="questionnumber === 3">
        <p>Question 3: What is your favorite flavour?</p>
        <button v-on:click="AFunc">Spicy</button>
        <button v-on:click="BFunc">Dull</button>
        <button v-on:click="CFunc">Light</button>
        <button v-on:click="DFunc">Rich</button>
      </div>
      <div v-if="questionnumber === 4">
        <p>Question 4: Where are you from? </p>
        <button v-on:click="AFunc">America</button>
        <button v-on:click="BFunc">Artic</button>
        <button v-on:click="CFunc">Gray</button>
        <button v-on:click="DFunc">China</button>
      </div>
      <div v-if="questionnumber === 5">
        <p>Question 5: What power do you prefer?</p>
        <button v-on:click="AFunc">Fire</button>
        <button v-on:click="BFunc">Heal</button>
        <button v-on:click="CFunc">Wind</button>
        <button v-on:click="DFunc">Rock</button>
      </div>
      <button v-if="questionnumber === 6" v-on:click="SFunc">Submit</button>
<!-- Element Bender Comments -->
      <p v-if="AWin === 1" class="comment"> RESULT: FIRE BENDER </p>
      <p v-if="BWin === 1" class="comment"> RESULT: WATER BENDER </p>
      <p v-if="CWin === 1" class="comment"> RESULT: AIR BENDER</p>
      <p v-if="DWin === 1" class="comment"> RESULT: EARTH BENDER </p>
    </div>
<!-- End of Div -->
  </div>


</template>

<script>
  export default {
    name: 'app',
    data () {
      return {
        displaynumber: 0,
        questionnumber: 1,
        lumberjacknumber: 1,
        bendernumber: 1,
        AOpt: 0,
        BOpt: 0,
        COpt: 0,
        DOpt: 0,
        AWin: 0,
        BWin: 0,
        CWin: 0,
        DWin: 0
      }
    },
    methods: {
      add: function () {
        this.displaynumber += 1
        this.questionnumber += 1
      },
      sub: function () {
        this.displaynumber -= 1
        this.questionnumber += 1
      },
      lumberjack: function () {
        this.lumberjacknumber += 1
      },
      bender: function () {
        this.bendernumber += 1
      },
      AFunc: function () {
        this.AOpt += 1
        this.questionnumber += 1
      },
      BFunc: function () {
        this.BOpt += 1
        this.questionnumber += 1
      },
      CFunc: function () {
        this.COpt += 1
        this.questionnumber += 1
      },
      DFunc: function () {
        this.DOpt += 1
        this.questionnumber += 1
      },
      SFunc: function () {
        if (this.AOpt > this.BOpt && this.AOpt > this.COpt && this.AOpt > this.DOpt) {
          this.AWin += 1
        } else if (this.BOpt > this.AOpt && this.BOpt > this.COpt && this.BOpt > this.DOpt) {
          this.BWin += 1
        } else if (this.COpt > this.AOpt && this.COpt > this.BOpt && this.COpt > this.DOpt) {
          this.CWin += 1
        } else if (this.DOpt > this.AOpt && this.DOpt > this.BOpt && this.DOpt > this.COpt) {
          this.DWin += 1
        }
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
  .comment {
    color: red;
  }

</style>
 