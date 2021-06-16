<template>
  <div id="app">
    <Home></Home>
  </div>
</template>



<script>
import Home from './Components/HomePage/Home/Home';
export default {
  name: 'App',
  components: {
    'Home': Home,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: end;
  color: #2c3e50;
}
*{
  padding: 0;
  margin: 0;
}
</style>
