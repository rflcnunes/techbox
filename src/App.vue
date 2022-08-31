<template>
  <div id="app">
    <AmHeader />
    <router-view />
  </div>
</template>

<script>
// @ is an alias to /src
import AmHeader from './components/organisms/AmHeader.vue';

export default {
  name: 'App',
  components: {
    AmHeader
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
