<template>
<div v-bind:class="showGame">
    <p>This is an import for game logic</p>
    <ol id="Board">
        <li class="row"></li>
        <li>#Cols:{{nCols}}</li>
        <li>#Rows:{{nRows}}</li>
        <li>#Mines:{{nMines}} </li>
    </ol>
</div>
</template>
<script>
var cols, rows, mines;
var minesweeper = require('minesweeper');
cols = localStorage.getItem("cols");
rows = localStorage.getItem('rows');
mines = localStorage.getItem('mines');
var mineArray = minesweeper.generateMineArray({
    rows: 10,
    cols: 10,
    mines: 15
});
var board = new minesweeper.Board(mineArray);
var grid = board.grid();
var state = board.state();
export default {
    //name: "Board",
    props: ['showGame'],
    data: function data() {
        return {
            nCols: cols,
            nRows: rows,
            nMines: mines
        }
    }
}
</script>
<style>
.showme {
    display: block;
}
</style>
