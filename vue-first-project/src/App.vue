<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'app'
}
</script>

<style>
a, button, div {
  box-sizing: border-box;
}

body {
  margin: 0px;
  padding: 0px;
}

button {
  border-radius: 0px;
}

h1, h2 {
  margin: 0px;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
