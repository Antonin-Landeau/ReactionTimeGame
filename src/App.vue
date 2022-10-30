<template>
  <h1>Reaction Game</h1>
  <button class="play-buttton" @click="startGame" v-if="!isPlaying">Play</button>
  <div v-if="isPlaying">
    <ReactionZone :delay="delay" @endGame="endGame" />
  </div>
  <div v-if="isEnded">
    <Result :score="score"/>
  </div>
</template>

<script>
import ReactionZone from "./components/ReactionZone.vue";
import Result from "./components/Result.vue";

export default {
  name: "App",
  components: {
    ReactionZone,
    Result,
  },
  data() {
    return {
      isPlaying: false,
      isEnded: false,
      delay: null,
      score: null,
    };
  },
  methods: {
    startGame () {
      this.isEnded = false
      this.delay = 2000 + Math.random() *5000
      this.isPlaying = true
    },
    endGame (score) {
      this.score = score;
      this.isEnded = true
      this.isPlaying = false
    }
  },
};
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
button{
  background-color: aquamarine;
  border: none;
  padding: 10px 20px;
  border-radius: 4px;
  color: #2c3e50;
  font-weight: 600;
}
button:hover {
  cursor: pointer;
}
</style>
