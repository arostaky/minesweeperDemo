<template>
<div class="container">
  <state-component :state="state"></state-component>
  <board-component :grid="grid"></board-component>
</div>
</template>

<script>
var cols, rows, mines;
cols = localStorage.getItem("cols");
rows = localStorage.getItem('rows');
mines = localStorage.getItem('mines');
if (cols == 'null' || rows == 'null' || mines == 'null') {
  cols = 10;
  rows = 10;
  mines = 5;
}
var minesweeper = require('minesweeper')
var _ = require('underscore')

// components
var StateComponent = require('./gamestate.vue')
var BoardComponent = require('./grid.vue')

var ma = minesweeper.generateMineArray({
  rows: rows,
  cols: cols,
  mines: mines
})
var board = new minesweeper.Board(ma)
var grid = board.grid()
var state = board.state()
export default {
  data() {
    return {
      grid: {
        data: grid
      },
      state: {
        data: state
      }
    }
  },
  components: {
    StateComponent,
    BoardComponent
  },
  events: {
    updated: function(x, y) {
      board.openCell(x, y)
      this.$set('grid', {
        data: []
      })
      var self = this
      setTimeout(function() {
        self.$set('grid', {
          data: grid
        })
        self.$set('state', {
          data: state
        })
      }, 0)
    }
  }
}
</script>
