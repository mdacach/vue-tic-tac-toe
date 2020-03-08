<template>
  <div id="header">
    <h1 id="header-text">Tic Tac Toe</h1>
  </div>
</template>

<script>
export default {
  name: "Header"
};
</script>

<style>
#header-text {
  font-family: Maven, fantasy;
  font-weight: bold;
  font-size: 250%;
  color: #d4cdcd;
}

#header {
  background-color: var(--terciary-color);
  width: 60%;
  text-align: center;
  margin: 0 auto;
  margin-bottom: 30px;
  padding: 2px;
  border-radius: 10px;
}
</style>