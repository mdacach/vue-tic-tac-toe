<template>
  <div
    @click="markComplete"
    class="cell"
    :class="{x: cell.marker=='x', 
    o:cell.marker=='o'}"
  >
  <p>
    {{ cell.id }}
  </p>
  </div>
</template>

<script>
export default {
  name: "Cell",
  props: ["cell", "turn", "gameOver"],
  data() {
    return {
      marked: false
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
p {
  font-size: 80px; 
  text-align: center;
}
.cell {
  width: 100%;
  height: 100%;
  background-color: pink;
  border: solid gray 2px;
}
.x {
  background-color: blue;
}
.o {
  background-color: red;
}
</style>