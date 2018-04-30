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
      this.whacks = 0;
      this.gameActive = true;
      this.deactivateAllMoles();
      this.startTimer();
      this.startMoles();
    },
    endRound: function () {
      const { whacks, highScore } = this;
      this.stopTimer();
      this.stopMoles();
      this.deactivateAllMoles();
      this.highScore = Math.max(whacks, highScore);
      this.gameActive = false;
    },

    // timer logic
    startTimer: function () {
      this.timerInterval = setInterval(this.decrementTime.bind(this), 1000);
    },
    stopTimer: function () {
      clearInterval(this.timerInterval);
    },
    startMoles: function () {
      this.moleInterval = setInterval(this.activateRandomMole.bind(this), 500);
    },
    stopMoles: function () {
      clearInterval(this.moleInterval);
    },
    decrementTime: function () {
      this.timer = this.timer - 1;
      if (this.timer === 0) {
        this.endRound();
      }
    },

    // mole logic
    incrementWhacks: function (moleId) {
      const moles = this.moles.slice();
      moles[moleId] = false;
      this.whacks = this.whacks + 1;
      this.moles = moles;
    },
    activateRandomMole: function () {
      const randomMoleIndex = Math.floor(Math.random() * this.moles.length);
      if (!this.moles[randomMoleIndex]) {
        this.activateMole(randomMoleIndex);
      }
    },
    activateMole: function (id) {
      const moles = this.moles.slice();
      moles[id] = true;
      this.moles = moles;
      setTimeout(() => this.deactivateMole(id), 1500);
    },
    deactivateMole: function (id) {
      const moles = this.moles.slice();
      moles[id] = false;
      this.moles = moles;
    },
    deactivateAllMoles: function () {
      this.moles = this.moles.map(() => false);
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
