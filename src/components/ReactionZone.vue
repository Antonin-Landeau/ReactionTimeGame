<template>
  <p class="consigne">
    Cliques le plus rapidement possible sur la zone verte qui va
    apparaitre d'ici peut pour calculer ton taux de réaction
  </p>
  <div v-if="isReady" @click="stopTimer" class="zone">Click me</div>
</template>

<script>
export default {
  name: "reactionZone",
  props: {
    delay: Number,
  },
  data() {
    return {
      isReady: false,
      score: 0,
      timer: null,
    };
  },
  mounted() {
    setTimeout(() => {
      this.isReady = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.score += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("endGame", this.score);
    },
  },
};
</script>

<style>
.zone {
  width: 50%;
  background-color: aquamarine;
  margin: 10px auto;
  padding: 79px;
  border-radius: 10px;
  font-weight: 600;
}
.consigne {
  max-width: 250px;
  margin: auto;
  padding: 10px;
}
</style>
