<template>
  <div v-bind:class="classObject">
    <Mole
      v-for="(moleState, idx) in moles"
      v-bind:key="idx"
      v-bind:active="moleState"
      v-bind:id="idx"
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
      this.$emit('whack', moleId);
    }
  },
  computed: {
    classObject: function () {
      return {
        moles: true,
        'game-active': !!this.gameActive,
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
