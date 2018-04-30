<template>
  <div v-bind:class="['single-counter', 'counter' + name]">
    <h2>{{ name }}:</h2>
    <h1>{{ count }}</h1>
  </div>
</template>

<script>
export default {
  name: 'Counter',
  props: ['name', 'count'],
}
</script>

<style scoped>

</style>
