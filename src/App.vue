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
      Open the Console, then click me!
    </button>
    <div class="counters-container">
      <!-- Create 3 counters here! -->
    </div>
    <!-- render your moles container here! -->
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
    startRound: function() {
      console.log('========= woah! =========');
      console.log('Take a look at App.vue line 9 and line 42');
      console.log('this is how you get something to run after a click!');
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
