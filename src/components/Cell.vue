<template>
  <div @click="markComplete" class="cell" :class="{x: cell.marker=='x', 
    o:cell.marker=='o'}"></div>
</template>

<script>
import { EventBus } from "../main";

export default {
  name: "Cell",
  props: ["cell", "turn", "gameOver"],
  data() {
    return {
      marked: false,
      marker: this.cell.marker
    };
  },
  methods: {
    markComplete() {
      if (!this.isMarked() && !this.gameOver) {
        this.cell.marker = this.turn;
        EventBus.$emit("marked", this.cell.id);
      }
    },
    isMarked() {
      return this.cell.marker;
    },
    resetCell() {
      this.marked = false;
      this.marker = this.cell.marker;
    }
  },
  created() {
    EventBus.$on("newGame", this.resetCell);
  }
};
</script>

<style >
.cell {
  box-sizing: border-box;
  width: 100%;
  height: 100%;
  background-color: var(--secundary-color);
  border: solid #d4cdcd 2px;
}

.cell:hover {
  opacity: 0.9;
}

.x {
  background-color: var(--primary-color);
}
.o {
  background-color: var(--terciary-color);
}
</style>