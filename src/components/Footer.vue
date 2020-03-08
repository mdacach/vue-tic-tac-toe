<template>
  <div id="footer">
    <h1 id="winner" v-if="gameOver">{{ display }}</h1>
    <button v-if="gameOver" @click="emitNewGame">new game</button>
  </div>
</template>

<script>
import { EventBus } from "../main";

export default {
  name: "Footer",
  props: ["gameOver", "winner"],
  data() {
    return {
      display: ""
    };
  },
  methods: {
    emitNewGame() {
      EventBus.$emit("newGame");
    },
    createDisplay(winner) {
      if (winner === "draw") {
        this.display = "It was an incredible draw!";
      } else if (winner === "x") {
        this.display = "Black absolutely destroyed.";
      } else if (winner === "o") {
        this.display = "Red crushed the game.";
      }
    }
  },
  created() {
    EventBus.$on("gameOver", winner => this.createDisplay(winner));
  }
};
</script>

<style>
#footer {
  width: 60%;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 70% 30%;
  justify-content: center;
  justify-items: center;
  position: relative;
}

#winner {
  position: relative;
  font-family: Maven, fantasy;
  font-weight: bold;
  color: #d4cdcd;
}

button {
  position: relative;
  top: 30%;
  margin: 0;
  background-color: var(--terciary-color);
  border: solid #d4cdcd 2px;
  border-radius: 10%;
  color: #d4cdcd;
  font-size: 16px;
  width: 6em;
  height: 2em;
  font-family: Maven, fantasy;
  font-weight: bold;
}
</style>