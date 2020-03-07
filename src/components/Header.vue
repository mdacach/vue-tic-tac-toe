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
  font-size: 250%;
  color: #d4cdcd;
}

#header {
  background-color: var(--terciary-color);
  width: 80%;
  text-align: center;
  margin: 0 auto;
  margin-bottom: 30px;
  padding: 2px;
  border-radius: 10px;
}
</style>