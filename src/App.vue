<template>
  <div id="app">
    <h1> ℒife-𝐴nswers.org</h1>  

<!-- Question Buttons -->
    <button v-on:click='tfquestions'>True/False Questions</button>
    <button v-on:click='mcquestions'>Multiple Choice Questions</button>
    <button v-on:click='ddquestions'>Dropdown Questions</button>
<!-- True/False Question Set -->
    <div v-if="tfnumber % 2 === 0" class="questionset">
      <img src="http://static.tvtropes.org/pmwiki/pub/images/lumberjack_5919.jpg" height="250px">
        <p v-if="questionnumber < 6"> Question: {{questionnumber}} </p>
        <p v-if="questionnumber === 1">Question 1: Do you like being outdoors.</p>
        <p v-if="questionnumber === 2">Question 2: Do you like to swing axes at trees? </p>
        <p v-if="questionnumber === 3">Question 3: Do you think you can fight a bear? </p>
        <p v-if="questionnumber === 4">Question 4: Do you make your own sandwiches? </p>
        <p v-if="questionnumber === 5">Question 5: Are you a big beared white sir? </p>
<!-- True/False Answers -->
        <button v-if="questionnumber <= 5"v-on:click="add">Yes</button>
        <button v-if="questionnumber <= 5"v-on:click="sub">No</button>
<!-- True/False Comments -->
        <p v-if="displaynumber === 5" class="comment"> Sounds like you're going to love working as a lumberjack! </p>
        <p v-if="displaynumber === 4" class="comment"> You may enjoy lumberjacking. </p>
        <p v-if="displaynumber === 3" class="comment"> You may enjoy lumberjacking. </p>
        <p v-if="displaynumber === 2" class="comment"> We may be on to something. </p>
        <p v-if="displaynumber === 1" class="comment"> We may be on to something. </p>
        <p v-if="displaynumber < 0" class="comment"> You probably don't want to be a lumberjack.</p>
        <p> Points: {{displaynumber}} </p>
      </div>

<!-- Multiple Choice Question Set -->
    <div v-if="mcnumber % 2 === 0" class="questionset">
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
      <div>
        <button v-if="questionnumber === 6" v-on:click="SFunc">Submit</button>
      </div>
<!-- Multiple Choice Comments -->
      <p v-if="AWin === 1" class="comment"> RESULT: FIRE BENDER </p>
      <p v-if="BWin === 1" class="comment"> RESULT: WATER BENDER </p>
      <p v-if="CWin === 1" class="comment"> RESULT: AIR BENDER</p>
      <p v-if="DWin === 1" class="comment"> RESULT: EARTH BENDER </p>
    </div>

<!-- Dropdown Question Set -->
    <div v-if="ddnumber % 2 === 0" class="questionset">
      <div>
      1.
        <select v-model="dropdownanswer">
          <option disabled value="">What do you enjoy most?</option>
          <option v-for="dropdown in dropdownset">
            {{dropdown.option}}</option>
        </select>
      </div>
      <div>
      2.
        <select v-model="dropdownanswer2">
          <option disabled value="">Where do you work?</option>
          <option v-for="dropdown in dropdownset2">
            {{dropdown.option}}</option>
        </select>
      </div>
      <div>
      3.
        <select v-model="dropdownanswer3">
          <option disabled value="">What is your tool of choice?</option>
          <option v-for="dropdown in dropdownset3">
            {{dropdown.option}}</option>
        </select>
      </div>
      <div>
      4.
        <select v-model="dropdownanswer4">
          <option disabled value="">Which game would you rather play? </option>
          <option v-for="dropdown in dropdownset4">
            {{dropdown.option}}</option>
        </select>
      </div>
      <div>
        5.
        <select v-model="dropdownanswer5">
          <option disabled value="">Which store would you rather shop at?</option>
          <option v-for="dropdown in dropdownset5">
            {{dropdown.option}}</option>
        </select>
        <div>
          <button v-on:click="DDFunc" class="ddbutton">Submit</button>
        </div>
        <div v-if='submit === "true"' class="border">
          <p>{{dropdowncomment}}</p>
          <p>{{dropdowncomment2}}</p>
          <p>{{dropdowncomment3}}</p>
          <p>{{dropdowncomment4}}</p>
          <p>{{dropdowncomment5}}</p>
        </div>
      </div>
    </div>

<!-- End of Div -->
  </div>
</template>

<script>
  export default {
    name: 'app',
    data () {
      return {
// Shared Question Data
        displaynumber: 0,
        questionnumber: 1,
        tfnumber: 1,
        mcnumber: 1,
        ddnumber: 1,
        AOpt: 0,
        BOpt: 0,
        COpt: 0,
        DOpt: 0,
        AWin: 0,
        BWin: 0,
        CWin: 0,
        DWin: 0,
// Dropdown Question Sets
        dropdownanswer: '',
        dropdownanswer2: '',
        dropdownanswer3: '',
        dropdownanswer4: '',
        dropdownanswer5: '',
        dropdowncomment: '',
        dropdowncomment1: '',
        dropdowncomment2: '',
        dropdowncomment3: '',
        dropdowncomment4: '',
        dropdowncomment5: '',
        submit: 'false',
        dropdownset: [
          {id: 1, option: 'Math'},
          {id: 2, option: 'Poetry'},
          {id: 3, option: 'Technology'},
          {id: 4, option: 'Cooking'}
        ],
        dropdownset2: [
          {id: 1, option: 'Construction Site'},
          {id: 2, option: 'Nature'},
          {id: 3, option: 'Office'},
          {id: 4, option: 'Kitchen'}
        ],
        dropdownset3: [
          {id: 1, option: 'Calculator'},
          {id: 2, option: 'Pen'},
          {id: 3, option: 'Laptop'},
          {id: 4, option: 'Spoon'}
        ],
        dropdownset4: [
          {id: 1, option: 'Puzzles'},
          {id: 2, option: 'Charades'},
          {id: 3, option: 'World of Warcraft'},
          {id: 4, option: 'Cooking Mama'}
        ],
        dropdownset5: [
          {id: 1, option: 'Staples'},
          {id: 2, option: 'Michaels'},
          {id: 3, option: 'NCIX'},
          {id: 4, option: 'Whole Foods'}
        ]
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
      tfquestions: function () {
        this.tfnumber += 1
        this.mcnumber = 1
        this.ddnumber = 1
      },
      mcquestions: function () {
        this.mcnumber += 1
        this.tfnumber = 1
        this.ddnumber = 1
      },
      ddquestions: function () {
        this.ddnumber += 1
        this.tfnumber = 1
        this.mcnumber = 1
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
      },
      DDFunc: function () {
        this.submit = 'true'
// Dropdown Question 1
        if (this.dropdownanswer === 'Math') {
          this.dropdowncomment = 'Math Club of Vancouver: 604-314-1596 - members@MCOV.com'
        } else if (this.dropdownanswer === 'Poetry') {
          this.dropdowncomment = 'Poetry District of Lower Mainland: 604-593-1023 - poetrydistrict@gmail.com'
        } else if (this.dropdownanswer === 'Technology') {
          this.dropdowncomment = 'Technology Club Van - 604-340-1337 - techvan@gmail.com '
        } else if (this.dropdownanswer === 'Cooking') {
          this.dropdowncomment = 'Lower Mainland Cooking Society - 604-203-4053 - cookingsocietylm@gmail.com'
        }
// Dropdown Question 2
        if (this.dropdownanswer2 === 'Construction Site') {
          this.dropdowncomment2 = 'Construction Club of Vancouver: 604-214-1396 - members@CCOV.com'
        } else if (this.dropdownanswer2 === 'Nature') {
          this.dropdowncomment2 = 'Nature District of Lower Mainland: 604-333-1323 - naturedistrict@gmail.com'
        } else if (this.dropdownanswer2 === 'Office') {
          this.dropdowncomment2 = 'Office Party Club Van - 604-240-1117 - officepartyvan@gmail.com '
        } else if (this.dropdownanswer2 === 'Kitchen') {
          this.dropdowncomment2 = 'Kitchen Design Society - 604-113-4044 - kdsocietylm@gmail.com'
        }
// Dropdown Question 3
        if (this.dropdownanswer3 === 'Calculator') {
          this.dropdowncomment3 = 'Calculator Speed Community of Vancouver: 604-231-1521 - members@CSCV.com'
        } else if (this.dropdownanswer3 === 'Pen') {
          this.dropdowncomment3 = 'Pen Collectors of Lower Mainland: 604-630-1003 - poetrydistrict@gmail.com'
        } else if (this.dropdownanswer3 === 'Laptop') {
          this.dropdowncomment3 = 'Computer Club YVR - 604-320-3201 - yvrcomps@gmail.com '
        } else if (this.dropdownanswer3 === 'Spoon') {
          this.dropdowncomment3 = 'Spoon Making Lower Mainland - 604-223-2223 - spoonmakers@gmail.com'
        }
// Dropdown Question 4
        if (this.dropdownanswer4 === 'Puzzles') {
          this.dropdowncomment4 = 'UBC Puzzle Club: 604-120-1221 - puzzles@UBC.com'
        } else if (this.dropdownanswer4 === 'Charades') {
          this.dropdowncomment4 = 'Boardgames Club of Lower Mainland: 604-620-1203 - boardgamesvan@hotmail.com'
        } else if (this.dropdownanswer4 === 'World of Warcraft') {
          this.dropdowncomment4 = 'UBC ESports Club - 604-230-3301 - ubcesports@UBC.com '
        } else if (this.dropdownanswer3 === 'Cooking Mama') {
          this.dropdowncomment4 = 'Cooking Fun Land - 604-102-COOK - cookingfunland@gmail.com'
        }
// Dropdown Question 5
        if (this.dropdownanswer5 === 'Staples') {
          this.dropdowncomment5 = 'Office Movie Nights - 604-221-1013 - officemovies@staples.com'
        } else if (this.dropdownanswer5 === 'Michaels') {
          this.dropdowncomment5 = 'Art Network of Vancouver: 604-770-1003 - artnetworkvan@gmail.com'
        } else if (this.dropdownanswer5 === 'NCIX') {
          this.dropdowncomment5 = 'Programming Club Van - 604-333-3101 - vanprogclub@gmail.com '
        } else if (this.dropdownanswer5 === 'Whole Foods') {
          this.dropdowncomment5 = 'Organic Jam Club - 604-223-JAMS - jamclub@jams.com'
        }
      }
    }
  }
</script>

<style>
  body {
    background-image: url("https://i.pinimg.com/originals/05/c8/2e/05c82ee619eb200c68e0789eb583ac73.png");
    background-size: 110%;
  }
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
  .questionset {
    margin-top: 100px;
  }

  button {
    float:top;
    margin-left:100px;
    margin-right:100px;
  }

  p{
    color:;
    font-weight:bolder;
  }

  .border {
    border: 1px solid #fff;
    border: 1px solid #fff;
    background-color: rgba(255,255,255,.8);
    padding: 5px;
    margin-left:15em;
    margin-right:15em;
    font-weight:bolder;
    font-size:20px;

  }
  select {
    height:3em;
    width: 40em;
    font-size:15px;
    border: 1px solid #fff;
    border: 1px solid #fff;
    background-color: rgba(255,255,255,.8);
    padding: 5px;
  }
</style>
 