<template>
  <div class="display">
      {{ value }}
  </div>
</template>

<script>
export default {
    props: ['value']
}
</script>

<style>
.display{
  grid-column: span 4;
  background-color: #4F4D50;
  border-radius: 5px;

  display:flex;
  justify-content: flex-start;
  align-items: center;
  padding: 25px;
  font-size: 2.2em;
  overflow: hidden;
  margin: 2px;
  box-shadow: 2px 2px 3px #00000050;
}
</style>