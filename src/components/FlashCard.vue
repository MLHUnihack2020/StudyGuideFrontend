<template>
  <div class="flex h-screen">
    <div class="shadow-lg p-5 rounded-lg w-auto h-64 w-24 m-auto mx-10">
      <div>
        <p v-if="cardSide == 0">{{ this.$parent.flashcards[cardNumber].question }}</p>
        <p v-if="cardSide == 1">{{ this.$parent.flashcards[cardNumber].answer }}</p>
      </div>
      <div>
        <button class="p-5" v-on:click="previous">Previous</button>
        <button class="p-5" v-on:click="flip">Flip</button>
        <button class="p-5" v-on:click="next">Next</button>
        <button class="p-5 pl-10" v-if="this.hintUsed === false && this.cardSide == 0" v-on:click="hint">Stuck? Get a hint.</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'FlashCard',
  data() {
    return {
      cardNumber: 0,
      cardSide: 0,
      hintUsed: false
    }
  },
  methods: {
    flip: function () {
      if (this.cardSide == 0) {
        this.cardSide = 1;
      } else {
        this.cardSide = 0;
      }
    },
    next: function () {
      if (this.cardNumber + 1 < this.$parent.flashcards.length) {
        this.cardNumber++;
        this.cardSide = 0;
        this.hintUsed = false;
      }
    },
    previous: function () {
      if (this.cardNumber - 1 >= 0) {
        this.cardNumber--;
        this.cardSide = 0;
      }
    },
    hint: function () {
      let hintLetter = this.$parent.flashcards[this.cardNumber].answer.charAt(0);
      let hintLetterLocation = this.$parent.flashcards[this.cardNumber].question.indexOf('_');

      let question = this.$parent.flashcards[this.cardNumber].question

      let newQuestion = question.substr(0, hintLetterLocation) + hintLetter + question.substr(hintLetterLocation, question.length)
      this.$parent.flashcards[this.cardNumber].question = newQuestion;
      this.hintUsed = true;
    }
  }
}
</script>
