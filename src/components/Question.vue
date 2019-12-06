<template>
  <!-- <div v-bind:id="[questionId]" style="display: none;"> -->
  <div class="question">
    <p id="questionText">{{ question.question }}</p>
    <p>{{  }}</p>
    <Answers
      v-for="answer in question.answers"
      v-bind:key="answer.id"
      v-bind:answer="answer"
    ></Answers>
  </div>
    
</template>

<script>
import Answers from './Answers.vue'

export default {
  name: 'question',
  components: {
    Answers
  },
  props: [
    'question'
  ],
  data () {
    return {
      questionId: 'question-' + this.question.id,
    }
  },
  methods: {
    resetAnswers () {
      var elements = document.getElementsByClassName("answerButton");

      for (var i = 0; i < elements.length; i++) {
        elements[i].innerHTML = i+1 + ".";
      }
    },
  },
  mounted () {
    this.resetAnswers()
  },
  updated() {
    this.resetAnswers()
  }

}
</script>

<style scoped>
#questionText{
  padding-bottom: 20px;
}
.question{
  font-size: 18pt;
  padding: 5px; 
}

</style>
