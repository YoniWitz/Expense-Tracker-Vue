<template>
  <div id="app">
    <ExpenseTracker msg="Simple expense manager project"/>
  </div>
</template>

<script>
import ExpenseTracker from './components/ExpenseTracker.vue'

export default {
  name: 'app',
  components: {
    ExpenseTracker
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>