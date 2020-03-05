<template>
  <div @click="markComplete" class="cell" :class="{x: cell.marker=='x', 
    o:cell.marker=='o'}"></div>
</template>

<script>
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
        this.$emit("marked", this.cell.id);
      }
    },
    isMarked() {
      return this.cell.marker;
    }
  }
};
</script>

<style >
.cell {
  width: 100%;
  height: 100%;
  background-color: var(--secundary-color);
  border: solid #d4cdcd 5px;
  border-radius: 5%;
}

.cell:hover {
  opacity: 0.8;
}

.x {
  background-color: var(--primary-color);
}
.o {
  background-color: var(--terciary-color);
}
</style>