<template>
  <div>
    <!-- TODO: render 4 Mole components -->
  </div>
</template>

<script>
// we need to import and include other components we will use within any given component
import Mole from './Mole';

export default {
  name: 'Moles',
  components: {
    Mole
  }
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
