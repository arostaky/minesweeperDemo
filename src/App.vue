<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h1>{{msg}}</h1>
    <h2>Set options bellow:</h2>
    <div id="inputbox">
      <label># Cols: <input type="number" name="cols" value=""></label>
      <br><br>
      <label># Rows: <input type="number" name="rows" value=""></label>
      <br><br>
      <label># Mines: <input type="number" name="mines" value=""></label>
      <br><br>
      <button>Start</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      msg: 'Mine Sweeper Demo'
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
#inputbox{
  width: 300px;
  margin: 0 auto;
}
input{width: 50px}
</style>
