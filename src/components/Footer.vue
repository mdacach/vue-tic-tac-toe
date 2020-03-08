<template>
  <div id="footer">
    <button v-if="gameOver" @click="emitNewGame">new game</button>
  </div>
</template>

<script>
import { EventBus } from "../main";

export default {
  name: "Footer",
  props: ["gameOver"],
  methods: {
    emitNewGame() {
      EventBus.$emit("newGame");
    }
  }
};
</script>

<style>
button {
  display: flex;
  margin: 0 auto;
  margin-top: 15px;
  margin-left: 73%;
  background-color: var(--terciary-color);
  border: solid #d4cdcd 2px;
  border-radius: 10%;
  color: #d4cdcd;
  width: 10%;
  height: 3%;
  justify-content: center;
  font-family: Maven, fantasy;
  font-weight: bold;
  font-size: 14px;
}
</style>