<template>
  <div v-bind:class="classObject">
    <Mole
      v-for="(moleState, idx) in [0, 1]"
      v-bind:key="idx"
      v-on:whack="handleWhack"
    >
    </Mole>
  </div>
</template>

<script>
import Mole from './Mole';

export default {
  name: 'Moles',
  components: {
    Mole
  },
  props: ['gameActive', 'moles'],
  methods: {
    handleWhack: function (moleId) {

    }
  },
  computed: {
    classObject: function () {
      return {
        moles: true,
        'game-active': true // fix me
      }
    }
  },
}
</script>

<style scoped>
.moles {
  display: flex;
  justify-content: space-between;
  opacity: 0.5;
  transition: opacity 0.3s ease;
}

.moles.game-active {
  opacity: 1;
}
</style>
