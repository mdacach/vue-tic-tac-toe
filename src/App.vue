<template>
  <div id="app">
    <Header />

    <Cells :gameOver="gameOver" :turn="turn" :cells="cells" @marked="nextTurn" @gameOver="endGame"></Cells>
  </div>
</template>

<script>
import Header from "./components/Header";
import Cells from "./components/Cells";

// creating the 9 cells initially with no marker
let cells = [];
for (let i = 1; i <= 9; i++) {
  cells.push({ id: i, marker: "" });
}

export default {
  name: "App",
  components: {
    Header,
    Cells
  },
  data() {
    return {
      cells: cells,
      turn: "x",
      gameOver: false
    };
  },
  methods: {
    nextTurn() {
      this.turn === "x" ? (this.turn = "o") : (this.turn = "x");
    },
    endGame(winner) {
      this.gameOver = true;
      if (winner == "draw") {
        console.log("you drawww omg");
      } else {
        console.log("congratulations!!!!!!!!!");
        console.log(winner + " won greatly!");
      }
    }
  }
};
</script>

<style>
:root {
  --primary-color: #1a1a1c;
  --secundary-color: #4e4e50;
  --terciary-color: #960641;
}

body {
  background-color: var(--primary-color);
}

#app {
  /* serve as a container */
  height: 60vw;
  width: 60vw;
  margin: 0 auto;
  position: relative;
}
</style>
