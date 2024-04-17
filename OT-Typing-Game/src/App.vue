<script>
export default {
  data() {
    return {
      currentWordIndex: 0,
      amountCorrect: 0,
      userInput: '', // to hold user input
      wordsObject: {
        word1: "BANANA",
        word2: "CHERRY",
        word3: "DOLPHIN",
        word4: "ELEPHANT",
        word5: "FLAMINGO",
        word6: "GIRAFFE",
        word7: "HIPPOPOTAMUS",
        word8: "IGLOO",
        word9: "JELLYFISH",
        word10: "KANGAROO",
        word11: "LION",
        word12: "MONKEY",
        word13: "NARWHAL",
        word14: "OCTOPUS",
        word15: "PENGUIN",
        word16: "QUARTZ",
        word17: "RACCOON",
        word18: "SQUIRREL",
        word19: "TURTLE",
        word20: "UNICORN"
      }
    };
  },
  methods: {
    checkWord() {
      const currentWordKey = `word${this.currentWordIndex + 1}`;
      if (this.userInput.toUpperCase() === this.wordsObject[currentWordKey]) {
        this.amountCorrect ++
        alert('Correct!');
        this.moveToNextWord();
      } else {
        alert('Try again!');
      }
      this.userInput = '';  // Clear input after check
    },
    moveToNextWord() {
      this.currentWordIndex = (this.currentWordIndex + 1) % 20;  // Cycle through the words
    }
  }
}
</script>


<template>
  <div class="divider-one">
    <h5 class="title">Let's Play a Game!</h5>
    <button v-on:click="moveToNextWord()" class="new-word-button">Click For a New Word!</button>
    <h2 class="wordsObjectColor">{{ wordsObject['word' + (currentWordIndex + 1)] }}</h2>
    <h1 class="correctAmount">Correct Amount: {{ amountCorrect }}</h1>
    <input type="text" class="answer" v-model="userInput" @keyup.enter="checkWord">
    <br>
     <br>
    <button v-on:click="checkWord()">Check Word</button>
    
  </div>
  <button @click="checkWord">Check Word</button>
</template>


<style>
.correctAmount{
  color: rgb(118, 118, 208);
}
.divider-one{
  margin-bottom: 1000px;
}
.title {
  display: flex;
  justify-content: center;
  font-size: 50px;
  margin-bottom: 20px; 
}

.new-word-button {
  background-color: #4CAF50; 
  color: white; 
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.wordsObjectColor{
  color: #4CAF50;
  font-size: 80px;
}
.answer{
  /* display: flex; */
  border-radius: 5px;
  width: 800px;
  height: 145px;
  font-size: 100px;
}
</style>
