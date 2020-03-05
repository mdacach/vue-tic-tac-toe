<template>
  <div id="app">
    <Cells :turn="turn" :cells="cells" @marked="nextTurn"></Cells>
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
      turn: "x"
    };
  },
  methods: {
    nextTurn() {
      this.turn === "x" ? (this.turn = "o") : (this.turn = "x");
    }
  }
};
</script>

<style>
</style>
