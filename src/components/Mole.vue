<template>
  <div class="mole-container active">
    <div class="mole-image-container">
      <img
        v-on:click="handleClick"
        class="mole"
        src="../assets/mole.png"
        alt="mole"
      />
    </div>
    <img
      class="dirt"
      src="../assets/dirt.svg"
      alt="mole dirt"
    />
  </div>
</template>

<script>
export default {
  name: 'Mole',
  props: ['active', 'id'],
  methods: {
    handleClick: function () {
      if (this.active) {
        this.$emit('whack', this.id);
      }
    }
  },
  computed: {
    classObject: function () {
      // use classObject to dynamically render class names based on props
      // add the "active" or "inactive" class, based on the 'active' prop passed in
    }
  }
}
</script>

<style scoped>
.mole-container {
  width: 160px;
  height: 160px;
  display: inline-block;
  margin: 10px;
  position: relative;
}

.mole-image-container {
  overflow: hidden;
  width: 160px;
  height: 140px;
}

.mole-container img {
  display: block;
  transition: all 0.3s ease;
}

.mole {
  position: relative;
  width: 60%;
  margin: auto;
  cursor: pointer;
}

.mole-container.active .mole {
  top: 0px;
}

.mole-container.inactive .mole {
  top: 200px;
}

.dirt {
  width: 100%;
  margin: auto;
  z-index: 1;
  position: absolute;
  bottom: 0;
}
</style>
