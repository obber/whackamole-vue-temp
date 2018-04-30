<template>
  <div class="single-counter">
    <h2>Counter Name:</h2>
    <h1>35</h1>
  </div>
</template>

<script>
export default {
  name: 'Counter',
  props: ['name', 'count'],
}
</script>

<style scoped>
.single-counter {
  border: 1px solid black;
  margin-top: 20px;
  padding: 20px;
}

.single-counter h1,
.single-counter h2 {
  margin: 0;
  text-align: center;
}

.single-counter h1 {
  font-size: 2.5em;
  margin: 0;
}
</style>
