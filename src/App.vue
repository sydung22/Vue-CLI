<template>
  <div>
    <Header></Header>
    <tabs></tabs>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Tabs from './components/tabs/Tabs.vue'

export default {
  name: 'App',
  components: {
    Header,
    Tabs,
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
