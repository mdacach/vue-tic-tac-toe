<template>
  <div id="app">
    <Cells :gameOver="gameOver" :turn="turn" :cells="cells" @marked="nextTurn" @gameOver="endGame"></Cells>
  </div>
</template>

<script>
import Cells from "./components/Cells";

// creating the 9 cells initially with no marker
let cells = [];
for (let i = 1; i <= 9; i++) {
  cells.push({ id: i, marker: "" });
}

export default {
  name: "App",
  components: {
    Cells
  },
  data() {
    return {
      cells: cells,
      turn: "x",
      gameOver: false, 
    };
  },
  methods: {
    nextTurn() {
      this.turn === "x" ? (this.turn = "o") : (this.turn = "x");
    },
    endGame(winner) {
      this.gameOver = true; 
      if (winner == 'draw') {
        console.log("you drawww omg");
      }
      else {
        console.log("congratulations!!!!!!!!!");
        console.log(winner + " won greatly!");

      }

    }
  }
};
</script>

<style>
</style>
