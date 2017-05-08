<template>
  <div id="app">
    <div v-bind:class="hideOpts">
    <img src="./assets/logo.png" width="128" height="128">
    <h1>{{msg}}</h1>
    <h2>Set options bellow:</h2>
    <div id="inputbox">
      <label># Cols: <input type="number" name="cols" value="" required="You must set a #" min="0" max="100" step="5" v-on:input="nCols($event)"></label>
      <br><br>
      <label># Rows: <input type="number" name="rows" value="" required="You must set a #" min="0" max="100" step="5" v-on:input="nRows($event)"></label>
      <br><br>
      <label># Mines: <input type="number" name="mines" value="" required="You must set a #" min="0" max="100" step="1" v-on:input="nMines($event)"></label>
      <br><br>
      <button v-on:click="newGame">Start</button>
    </div>
  </div>
    <board></board>
</div>
</template>

<script>
import Board from './board.vue';
var cols, rows, mines;
export default {
  name: 'app',
  data () {
    return {
      msg: 'Mine Sweeper Demo',
      hideOpts:''
    }
  },
  methods:
    {
    newGame() {
      this.hideOpts='hideMe';
      this.$emit('newGame');
      this.$emit('setDiff', 1);
      //this.$root.$emit('newGame');
      //this.startGame = event.target.value;
      console.log('emmiting bus...');
    },
    nCols(event){
      cols = event.target.value;
      localStorage.setItem("cols", cols);
      console.log("# cols: "+ cols)
    },
    nRows(event){
      rows = event.target.value;
      localStorage.setItem("rows", rows);
      console.log("# rows: " + rows)
    },
    nMines(event){
      mines = event.target.value;
      localStorage.setItem("mines", mines);
      console.log('# mines: '+ mines)
    }
  },
  components: {
    Board
  }
}
</script>

<style lang="scss">
.hideMe{
  display: none;
}
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
