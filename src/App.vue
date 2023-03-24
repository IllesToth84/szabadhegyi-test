<template>
  <div id="app">
    <div class="container">
      <OverLay />
    </div>
  </div>
</template>

<script>
import OverLay from './components/OverLay';

export default {
  name: 'App',
  components: {
    OverLay,
  },
};
</script>

<style lang="scss">
#app {
  font-family: 'Arial', sans-serif;
}

.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: $default-black;

  .toggle-btn {
    position: absolute;
    top: 5%;
    right: 5%;
  }
}
</style>
