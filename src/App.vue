<template>
<div id="app">
  <h1>Calculadora Vue</h1>
  <Calculator/>

  <link href='https://fonts.googleapis.com/css?family=Source+Sans+Pro' rel='stylesheet' type='text/css'>
</div>
</template>

<script>
import Calculator from "./main/Calculator.vue"

export default {
  components: { Calculator },

}
</script>

<style>
body{
  margin: 0;
  font-family:'Source Sans Pro', sans-serif;
}
#app {
  display: flex;
  flex-direction: column;
  height: 100vh;
  justify-content: center;
  align-items: center;
  text-align: center; 

  color: #fff;
  background: linear-gradient(to bottom,#8230C0,#170624);
}
</style>