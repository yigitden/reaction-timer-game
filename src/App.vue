<template>
  <div class="main">
    <h1>Reaction Timer Game</h1>
    <button @click="start" :disabled="isPlaying">Play</button>
    <Results v-if="showResult" :score="score" />
    <BlockFrame v-if="isPlaying" :delay="delay" @end="endGame" />
  </div>
</template>

<script>
import Results from "./components/Results.vue";
import BlockFrame from "./components/BlockFrame.vue";
export default {
  name: "App",
  data() {
    return {
      delay: null,
      isPlaying: false,
      score: null,
      showResult: false,
    };
  },
  methods: {
    start() {
      (this.isPlaying = true), (this.delay = 2000 + Math.random() * 5000);
      this.showResult = false;
    },
    endGame(time) {
      (this.score = time), (this.isPlaying = false);
      this.showResult = true;
    },
  },
  components: { BlockFrame, Results },
};
</script>

<style>
.main {
  text-align: center;
}
button {
  border: 0;
  border-radius: 4px;
  font-size: 20px;
  color: white;
  padding: 15px;
  background-color: #6fedd6;
  cursor: pointer;
}
button[disabled] {
  opacity: 0.3;
  cursor: not-allowed;
}
</style>
