<template>
  <div>
    <button class="letter" @click="$emit('start-game')">New Game</button>
  </div>
</template>

<script>
export default {
  name: "StartButton",
  data: function() {
    return {};
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.letter {
  display: block;
  font-size: 1em;
  font-weight: bold;
  color: white;
  background-color: rgb(12, 39, 90);
  margin: auto;
  width: 100px;
  height: 40px;
  border: 1px solid black;
  box-shadow: 1px 1px rgb(128, 128, 128);
  cursor: pointer;
}
</style>