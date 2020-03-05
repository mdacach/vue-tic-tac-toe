<template>
  <div id="container">
    <div v-for="cell in cells" :key="cell.id">
      <Cell :turn="turn" :cell="cell" @marked="$emit('marked')" />
    </div>
  </div>
</template>

<script>
import Cell from "./Cell";

export default {
  name: "Cells",
  components: {
    Cell
  },
  props: ["cells", "turn"]
};
</script>

<style>
#container {
  width: 50vw;
  height: 50vw;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(3, 1fr);
}
</style>