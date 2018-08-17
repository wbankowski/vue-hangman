<template>
  <div id="app">
   <h1>Hangman Game</h1>
   <div class="template" v-for="char in wordTemplate" :key="char"> {{ char }}</div>
   <hr>
   <keyboard @keypress="checkChar($event)"/>
   <hr>
   <start-button v-if=!isActive @start-game="startGame()"/>
  </div>
</template>

<script>
import Keyboard from "./components/Keyboard.vue";
import StartButton from "./components/StartButton.vue";

export default {
  name: "app",
  components: {
    Keyboard,
    StartButton
  },
  data: function() {
    return {
      isActive: false,
      counter: 0,
      clickedLetters: [],
      word: "HANGMAN",
      wordLetters: [],
      wordTemplate: [],
      wordsLibrary: ["AKCELIO", "JAVASCRIPT", "MONGODB", "DEVELOPER", "NODEJS"]
    };
  },
  methods: {
    startGame() {
      this.isActive = true;
      this.counter = 0;
      this.clickedLetters = [];
      this.word = this.getRandomWord();
      this.wordLetters = this.word.split("");
      this.wordTemplate = Array(this.word.length);
    },
    // randomWord() {
    //   let index = Math.floor(Math.random() * this.wordsLibrary.length);
    //   let word = this.wordsLibrary[index];
    //   return word;
    // },
    getRandomWord: async function getWord() {
      //await the response of the fetch call
      let response = await fetch(
        "https://api.wordnik.com/v4/words.json/randomWord"
      );
      //proceed once the first promise is resolved.
      let word = await response.json();
      //proceed only when the second promise is resolved
      return word;
    },
    checkChar(letter) {
      if (this.clickedLetters.includes(letter)) return;
      this.clickedLetters.push(letter);
      for (let i = 0; i < this.wordTemplate.length; i++) {
        if (letter === this.wordLetters[i]) {
          this.wordTemplate.splice(i, 1, letter);
        }
      }
    }
  }
};
</script>

<style>
#app {
  text-align: center;
}

.template {
  display: inline-flex;
  flex-direction: row;
  flex-wrap: wrap;
  margin: 3px;
  width: 40px;
  height: 40px;
  border: 1px solid black;
  justify-content: center;
  align-items: center;
}
</style>
