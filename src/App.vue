<template>
  <div id="app">
    <index></index>
  </div>
</template>

<script>
import index from './index.vue'

export default {
  name: 'app',
  
  components: { index, },
};
</script>

<style lang="scss">
html, body {
  padding: 0;
  margin: 0;
}

#app {
  width: 100vw;
  height: 100vh;
  position: relative;
}
</style>