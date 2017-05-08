<template>
<div class="container">
  <div class="row" v-for="row in grid.data" :row="row">
    <div v-for="cell in row" :key="cell" class="col-xs-1" v-on:click="newState($event)">
      {{status}}
    </div>
  </div>
</div>
</template>
<script>
var {
  CellStateEnum,
  CellFlagEnum
} = require('minesweeper');

var cellState = function(cell) {
  if (cell.state === CellStateEnum.CLOSED) {
    if (cell.flag === CellFlagEnum.NONE) {
      return 'X'
    } else if (cell.flag === CellFlagEnum.EXCLAMATION) {
      return '!'
    } else if (cell.flag === CellFlagEnum.QUESTION) {
      return '?'
    }
  } else if (cell.state === CellStateEnum.OPEN) {
    if (cell.isMine) {
      return '*'
    } else {
      return cell.numAdjacentMines === 0 ?
        ' ' :
        cell.numAdjacentMines.toString()
    }
  }
}
export default {
  props: ['grid'],
  data(){
    return {
      //status: cellState(this.cell)
      status: 'X|Y'
    }
  },
  methods: {
    newState: function(event) {
      var whatis = event.target.value;
      console.log('what is: '+ whatis);
      console.log('cellstate: '+ cellState(this));
      //this.$emit('updated', this.cell.x, this.cell.y);
      console.log('emitting event...')
    }
  }
}
</script>
