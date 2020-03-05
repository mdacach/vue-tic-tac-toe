<template>
  <div id="header">
    <h1>Tic Tac Toe</h1>
  </div>
</template>

<script>
export default {
  name: "Header"
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Maven+Pro:400,900&display=swap");

h1 {
  font-family: Maven, fantasy;
  font-weight: bold;
  font-size: 55px;
  color: #d4cdcd;
}

#header {
  background-color: var(--terciary-color);
  width: 800px;
  padding: 10px;
  text-align: center;
  border-radius: 10px;
  margin: 0 auto;
  margin-bottom: 20px;
}
</style>