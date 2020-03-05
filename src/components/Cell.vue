<template>
  <div
    @click="markComplete"
    class="cell"
    :class="{x: cell.marker=='x', 
    o:cell.marker=='o'}"
  >{{cell.id}}</div>
</template>

<script>
export default {
  name: "Cell",
  props: ["cell", "turn"],
  methods: {
    markComplete() {
      this.cell.marker = this.turn;
      this.$emit("marked");
    }
  }
};
</script>

<style >
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