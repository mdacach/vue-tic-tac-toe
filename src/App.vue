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
let createCells = function() {
  let cells = [];
  for (let i = 1; i <= 9; i++) {
    cells.push({ id: i, marker: "" });
  }

  return cells;
};

export default {
  name: "App",
  components: {
    Header,
    Cells,
    Footer
  },
  data() {
    return {
      cells: createCells(),
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
    resetApp() {
      this.cells = createCells();
      this.turn = "x";
      this.gameOver = false;
    }
  },

  created() {
    EventBus.$on("marked", this.nextTurn);
    EventBus.$on("gameOver", this.endGame);
    EventBus.$on("newGame", this.resetApp);
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
