<template>
  <div class="">
    <span v-if="cardSide == 0">{{ this.$parent.flashcards[cardNumber].question }}</span>
    <span v-if="cardSide == 1">{{ this.$parent.flashcards[cardNumber].answer }}</span>
    <button v-on:click="previous">Previous</button>
    <button v-on:click="flip">Flip</button>
    <button v-on:click="next">Next</button>
  </div>
</template>

<script>
export default {
  name: 'FlashCard',
  data() {
    return {
      cardText: "",
      cardNumber: 0,
      cardSide: 0
    }
  },
  methods: {
    flip: function () {
      this.cardText = "ye";
      if (this.cardSide == 0) {
        this.cardSide = 1;
      } else {
        this.cardSide = 0;
      }
    },
    next: function () {
      this.cardNumber++;
    },
    previous: function () {
      this.cardNumber--;
    }
  }
}
</script>
