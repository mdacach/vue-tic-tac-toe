<template>
  <div id="app">
    <Header />

    <Cells :gameOver="gameOver" :turn="turn" :cells="cells"></Cells>

    <Footer :gameOver="gameOver"></Footer>
  </div>
</template>

<script>
import Header from "./components/Header";
import Cells from "./components/Cells";
import Footer from "./components/Footer";
import { EventBus } from "./main.js";

// creating the 9 cells initially with no marker
let cells = [];
for (let i = 1; i <= 9; i++) {
  cells.push({ id: i, marker: "" });
}

export default {
  name: "App",
  components: {
    Header,
    Cells,
    Footer
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
    },
    newGame() {
      this.gameOver = false;
      this.turn = "x";
      this.resetGrid();
    },
    resetGrid() {
      let cells = [];
      for (let i = 1; i <= 9; i++) {
        cells.push({ id: i, marker: "" });
      }
      this.cells = cells;
    }
  },
  created() {
    EventBus.$on("marked", this.nextTurn);
    EventBus.$on("gameOver", this.endGame);
    EventBus.$on("newGame", this.newGame);
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Maven+Pro:400,900&display=swap");

:root {
  --primary-color: #1a1a1c;
  --secundary-color: #4e4e50;
  --terciary-color: #960641;
}

body {
  background-color: var(--primary-color);
  font-family: Maven, fantasy;
}

#app {
  /* serve as a container */
  height: 60vw;
  width: 60vw;
  margin: 0 auto;
  position: relative;
}
</style>
