<template>
  <div id="app">

    <div class="grid-container">
      <div class="grid-item logo"><img src="./assets/ff_logo.png"></div>
      <div class="grid-item team1"><Left /></div>
      <div class="grid-item team2"><Right /></div>
      <div class="grid-item question">
        <Question
          
          v-bind:question="nextQuestion"
        ></Question>

        <span v-if="nextQuestion.id > 1"><b-button type="is-light" class="navButton" @click="backQuestion">back</b-button></span>
        <span v-if="nextQuestion.id < this.questions.length"><b-button type="is-light" class="navButton" @click="setQuestion">next</b-button></span>
      </div>
    </div>

  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Left from './components/Left.vue'
import Right from './components/Right.vue'
import Question from './components/Question.vue'

export default {
  name: 'app',
  components: {
    // HelloWorld
    Left,
    Right,
    Question,
  },
  methods: {
    setQuestion() {
      this.nextQuestion = this.questions[this.counter]
      this.counter++
      this.resetAnswers
    },
    backQuestion() {
      this.nextQuestion = this.questions[this.counter - 2]
      this.counter--
    },
  },
  computed: {
    getFirstQuestion() {
      console.log(this.questions)
    }
  },
  mounted () {
    this.setQuestion()
  },
  data () {
    return {
      nextQuestion: null,
      counter: 0,
      questions: [
        { id: 1, question: 'Tell me something many people do just once a week', answers: [
          { id: 1, answer: 'Church', votes: 35 },
          { id: 2, answer: 'Groceries/Shopping', votes: 25 },
          { id: 3, answer: 'Laundry', votes: 10 },
          { id: 4, answer: 'Clean House', votes: 10 },
          { id: 5, answer: 'Sleep in', votes: 5 },
          { id: 6, answer: 'Eat out', votes: 5 },
        ]},
        { id: 2, question: 'Name something that breaks down', answers: [
          { id: 1, answer: 'Car', votes: 45 },
          { id: 2, answer: 'Body', votes: 20 },
          { id: 3, answer: 'Computer', votes: 15 },
          { id: 4, answer: 'Communication', votes: 10 },
          { id: 5, answer: 'Foreign relations', votes: 5 },
          { id: 6, answer: 'TV', votes: 5 },
        ]},
        { id: 3, question: 'Name something you never leave home without',answers: [
          { id: 1, answer: 'Cell phone', votes: 45 },
          { id: 2, answer: 'Purse', votes: 30 },
          { id: 3, answer: 'Wallet', votes: 10 },
          { id: 4, answer: 'Keys', votes: 5 },
          { id: 5, answer: 'Money', votes: 5 },
          { id: 6, answer: 'Kids', votes: 5 },
        ]},
        { id: 4, question: 'Other than wood, name a material that might be used when building a house',answers: [
          { id: 1, answer: 'Brick', votes: 35 },
          { id: 2, answer: 'Glass', votes: 20 },
          { id: 3, answer: 'Nails', votes: 20 },
          { id: 4, answer: 'Concrete', votes: 15 },
          { id: 5, answer: 'Steel', votes: 5 },
          { id: 6, answer: 'Plastic', votes: 5 },
        ]},
        { id: 5, question: 'Name a country with a name that starts with the letter A',answers: [
          { id: 1, answer: 'Australia', votes: 30 },
          { id: 2, answer: 'Afghanistan', votes: 25 },
          { id: 3, answer: 'Albania', votes: 20 },
          { id: 4, answer: 'Algeria', votes: 15 },
          { id: 5, answer: 'Argentina', votes: 5 },
          { id: 6, answer: 'Armenia', votes: 5 },
        ]},
      ],
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

.navButton {
  margin: 5px 5px 5px 5px;
}
.grid-container {
  display: grid;
  grid-template-columns: auto 50% auto;
  padding: 10px;
  /* height: 500px;  */
  align-content: center; 
}
.grid-item {
  text-align: center;
}
.logo {
  position: relative;
  bottom: 60px; 
  grid-column: 2;
  grid-row: 1 / span 1;
}
.team1 {
  position: relative;
  top: 200px;
  left: 50px;
  font-size: 30px;
  grid-column: 1;
  grid-row: 1 / span 3;
}
.team2 {
  position: relative;
  top: 200px;
  right: 50px;
  font-size: 30px;
  grid-column: 3; 
  grid-row: 1 / span 3;
}
.middle{
  grid-column: 2;
  grid-row: 1 / span 3; 
}
.question {
  position: relative;
  bottom: 20px;
  grid-column: 2; 
}
.answers {
  grid-column: 2
}
img {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 50%;
}

</style>
