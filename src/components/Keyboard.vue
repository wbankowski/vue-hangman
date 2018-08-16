<template>
  <div>
    <div class="keys" v-for="key in keyboard" :key="key" @click="$emit('keypress', key)"> {{ key }} </div>
  </div>
</template>

<script>
export default {
  name: "Keyboard",
  data: function() {
    return {
      keyboard: [
        "A",
        "Ą",
        "B",
        "C",
        "Ć",
        "D",
        "E",
        "Ę",
        "F",
        "G",
        "H",
        "I",
        "J",
        "K",
        "L",
        "Ł",
        "M",
        "N",
        "Ń",
        "O",
        "Ó",
        "P",
        "Q",
        "R",
        "S",
        "Ś",
        "T",
        "U",
        "V",
        "W",
        "X",
        "Y",
        "Z",
        "Ź",
        "Ż"
      ]
    };
  },
  props: {
    msg: String
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.keys {
  display: inline-flex;
  flex-direction: row;
  flex-wrap: wrap;
  margin: 3px;
  width: 40px;
  height: 40px;
  border: 1px solid black;
  box-shadow: 1px 1px grey;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}

.keys:hover {
  background-color: yellow;
}
</style>
