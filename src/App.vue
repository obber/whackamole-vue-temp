<template>
  <div id="whackamole" class="whackamole">
    <h1 class="logo">
      Whack-a-mole!
    </h1>
    <button
      class="start-game"
      text="Start Round"
      v-on:click="startRound"
    >
      Start Round
    </button>
    <div class="counters-container">
      <Counter
        name="Whacks"
        v-bind:count="whacks"
      ></Counter>
      <Counter
        name="High Score"
        v-bind:count="highScore"
      ></Counter>
      <Counter
        name="Timer"
        v-bind:count="timer"
      ></Counter>
    </div>
    <Moles
      v-bind:game-active="gameActive"
      v-bind:moles="moles"
      v-on:whack="incrementWhacks"
    ></Moles>
  </div>
</template>

<script>
import Counter from './components/Counter'
import Moles from './components/Moles'

export default {
  name: 'App',
  components: {
    Counter,
    Moles
  },
  data: () => {
    return {
      // counters
      whacks: 0,
      highScore: 0,
      timer: 0,
      // game state
      moles: [false, false, false, false],
      gameActive: false,
    };
  },
  methods: {
    // control game flow
    startRound: function () {
      this.timer = 20;
      this.whacks = undefined; // fix me
      this.gameActive = undefined; // fix me
      this.deactivateAllMoles();
      this.startTimer();
      this.startMoles();
    },
    endRound: function () {
      const { whacks, highScore } = this;
      this.stopTimer();
      this.stopMoles();
      this.deactivateAllMoles();
      this.highScore = 99; // fix me
      this.gameActive = undefined; // fix me
    },

    // timer logic
    startTimer: function () {

    },
    stopTimer: function () {

    },
    startMoles: function () {

    },
    stopMoles: function () {

    },
    decrementTime: function () {

    },

    // mole logic
    incrementWhacks: function (moleId) {

    },
    activateRandomMole: function () {

    },
    activateMole: function (id) {

    },
    deactivateMole: function (id) {

    },
    deactivateAllMoles: function () {

    }
  }
}
</script>

<style>
body {
  margin: 0;
  padding: 0;
  font-family: 'Bungee', cursive;
}

button {
  font-family: 'Bungee', cursive;
}

.whackamole {
  max-width: 800px;
  width: 100%;
  margin: auto;
  margin-top: 20px;
}

.start-game {
  margin: auto;
  display: block;
}

.logo {
  text-align: center;
  margin: 30px;
}

.counters-container {
  display: flex;
  justify-content: space-around;
  margin-bottom: 20px;
}

button {
  padding: 20px;
  border-radius: 3px;
  border: 0;
  background-color: #52b1d6;
  color: #fff;
  font-size: 1em;
  cursor: pointer;
  transition: background-color 0.2s ease;
}

button:hover {
  background-color: #72c9ea;
}
</style>
