<template>
  <div class="answer">
    <b-button type="is-info" class="answerButton" v-bind:id="[buttonId]" @click="showAnswer">{{ answer.answer }}</b-button>
  </div>
</template>

<script>


export default {
  name: 'app',
  components: {
    // HelloWorld
  },
  props: [
    'answer'
  ],
  methods: {
    showAnswer: function(event) {
      document.getElementById("answer-" + this.answer.id).innerText = this.answer.answer + " (" + this.answer.votes + ")"
      event.target.className = "button answerButton is-success"
    },
  },
  computed: {

  },
  data () {
    return {
      buttonId: 'answer-' + this.answer.id
    }
  },
  mounted() {
    // console.log(document.getElementById("answer-" + this.answer.id).innerText)
    // document.getElementById("answer-" + this.answer.id).innerText = this.answer.id + ".";
  },
}
</script>

<style scoped>
.answerButton{
  width: 250px; 
  margin: 5px 0 0 0; 
}

</style>
