<template>
  <div id="cells-container">
    <div v-for="cell in cells" :key="cell.id">
      <Cell
        :gameOver="gameOver"
        :turn="turn"
        :cell="cell"
        @marked="$emit('marked', cell.id); markGrid(cell.id); cellsMarked++; isGameOver(); "
      />
    </div>
  </div>
</template>

<script>
import Cell from "./Cell";

export default {
  name: "Cells",
  data() {
    return {
      // grid has 10 elts for we to order from 1 to 9
      grid: ["null", "", "", "", "", "", "", "", "", ""],
      cellsMarked: 0
    };
  },
  components: {
    Cell
  },
  props: ["cells", "turn", "gameOver"],

  methods: {
    equals3(board, marker) {
      return board.every(id => this.grid[id] === marker);
    },
    isGameOver() {
      const winningBoards = [
        [1, 2, 3],
        [4, 5, 6],
        [7, 8, 9],
        [1, 4, 7],
        [2, 5, 8],
        [3, 6, 9],
        [1, 5, 9],
        [3, 5, 7]
      ];

      for (let board of winningBoards) {
        if (this.equals3(board, "x")) {
          let winner = "x";
          this.$emit("gameOver", winner);
          return;
        } else if (this.equals3(board, "o")) {
          let winner = "o";
          this.$emit("gameOver", winner);
          return;
        }
      }
      if (this.cellsMarked === 9) {
        this.$emit("gameOver", "draw");
      }
    },
    markGrid(id) {
      this.grid[id] = this.turn;
    },
    showGrid() {
      console.log(this.grid);
    }
  }
};
</script>

<style>
#cells-container {
  box-sizing: border-box;
  width: 80%;
  height: 80%;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  margin: 0 auto;
  border: solid #d4cdcd 4px;
  border-radius: 2%;
}
</style>