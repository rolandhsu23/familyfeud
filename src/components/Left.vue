<template>
  <div>
    <h1>Team 1</h1>
    <p>Score: {{ score }} </p>   
    <b-button class="scoreButton" type="is-danger" @click="minusScore">-</b-button>  
    <b-button class="scoreButton" type="is-success" @click="addScore">+</b-button>
    <br>  
    <b-button rounded @click="resetScore">reset</b-button>
    <br>
    <span class="button xButton is-light" @click="toggleX">X</span>
    <span class="button xButton is-light" @click="toggleX">X</span>
    <span class="button xButton is-light" @click="toggleX">X</span>
    <audio id="buzzerSound" src="./buzz.mp3"></audio>
  </div>
</template>

<script>


export default {
  name: 'app',
  components: {

  },
  data () {
    return {
      score: 0        
    }
  },
  props: [

  ],
  methods: {
      addScore() {
          this.score += 5
      },
      minusScore() {
          this.score -= 5
      },
      resetScore() {
          this.score = 0
      },
      toggleX: function (event) {
        if(event.target.className == "button xButton is-light")
        {
          this.audio.play()
        	event.target.className = "button xButton is-danger";
        }
        else
        {
        	event.target.className = "button xButton is-light";
        }
      },
  },
  computed: {

  },
  mounted() {
    this.audio = document.getElementById('buzzerSound');
  },
}
</script>

<style scoped>
.scoreButton {
  font-size: 15pt;
  line-height: 5px;
  width: 30px;
  height: 30px; 
  margin: 0px 5px 0px 5px;
  text-align: center;
}
.xButton {
  width: 100px; 
  height: 100px;
  font-size: 50pt;
  line-height: 5px;
  margin: 5px 5px 5px 5px;
}

</style>
