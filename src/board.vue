<template>
<div v-bind:class="showGame">
  <p>This is an import for game logic</p>
  <ol id="Board">
    <li class="row"></li>
    <li>#Cols:{{nCols}}</li>
    <li>#Rows:{{nRows}}</li>
    <li>#Mines:{{nMines}} </li>
  </ol>
  <div id="grid">{{displayColHead}}</div>
  <div id="rows">{{displayRow}}</div>
</div>
</template>
<script>
var cols, rows, mines;
var minesweeper = require('minesweeper');
cols = localStorage.getItem("cols");
rows = localStorage.getItem('rows');
mines = localStorage.getItem('mines');
if (cols == 'null' || rows == 'null' || mines == 'null') {
  cols = 10;
  rows = 10;
  mines = 5;
}
var mineArray = minesweeper.generateMineArray({
  rows: rows,
  cols: cols,
  mines: mines
});
var BoardStateEnum = minesweeper.BoardStateEnum;
var CellStateEnum = minesweeper.CellStateEnum;
var CellFlagEnum = minesweeper.CellFlagEnum;
var strColHead,strRow;
//console.log('# of cols: ' + board.numCols());
var printBoard = function(board) {
  var i,
    grid = board.grid();
    strColHead = '   ';

  // print a header that shows the column numbers
  for (i = 0; i < board.numCols(); i++) {
    strColHead += '   ' + i + '   ';
  }
  console.log(strColHead);

  // print all the rows on the board
  for (i = 0; i < board.numRows(); i++) {
    printRow(grid[i], i);
  }
};
var printRow = function (rowArray, rowNum) {
  var i,
      cell;
      strRow = '';

  // Start the row with the row number
  strRow += rowNum !== undefined ? ' ' + rowNum + ' ' : '';

  // Add each cell in the row to the string we will print
  for (i=0; i<rowArray.length; i++) {
    cell = rowArray[i];
    if (cell.state === CellStateEnum.CLOSED) {
      if (cell.flag === CellFlagEnum.NONE) {
        strRow += getCellString(' ');
      } else if (cell.flag === CellFlagEnum.EXCLAMATION) {
        strRow += getCellString('!');
      } else if (cell.flag === CellFlagEnum.QUESTION) {
        strRow += getCellString('?');
      }
    } else if (cell.state === CellStateEnum.OPEN) {
      if (cell.isMine) {
        strRow += getCellString('*');
      } else {
        strRow += getCellString(cell.numAdjacentMines);
      }
    }
}

  // Print this row to the console
  console.log(strRow);
};
var getCellString = function (content) {
  return ' [ ' + content + ' ] ';
};
var board = new minesweeper.Board(mineArray);
var grid = board.grid();
var state = board.state();
printBoard(board);
export default {
  //name: "Board",
  props: ['showGame','strRow'],
  data: function data() {
    return {
      nCols: cols,
      nRows: rows,
      nMines: mines,
      displayColHead: strColHead,
      displayRow: strRow
    }
  }
}
</script>
<style>
.showme {
  display: block;
}
</style>
