<template>
  <div id="app">
    <CreatePurifier msg="Welcome to Your Advance Purifier"/>
  </div>
</template>

<script>
import CreatePurifier from './components/CreatePurifier.vue'

export default {
  name: 'App',
  components: {
    CreatePurifier
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
