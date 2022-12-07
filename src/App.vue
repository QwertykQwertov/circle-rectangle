<template>
  <div id="app">
    <Header />
    <Content />
    </div>
</template>

<script>
import Content from './components/content.vue'
import Header from './components/header.vue'

export default {
  name: 'App',
  components: {
    Content,
    Header,
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
  /* margin-top: 60px; */
}
body{
  margin: 0;
}
</style>
