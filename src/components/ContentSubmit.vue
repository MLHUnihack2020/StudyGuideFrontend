<template>
  <div class="">
    <p class="my-5 text-xl">Generate studying questions by pasting below.</p>

    <div>
      <textarea class="shadow-xl p-5 rounded-lg w-full h-72" id="inputText" name="inputText" v-model="$parent.inputText"></textarea>
    </div>
    <div>
      <button class="text-lg shadow-md px-3 py-2 rounded-lg font-bold m-5" v-on:click="sendRequest">Submit text</button>
      <button class="text-lg shadow-md px-3 py-2 rounded-lg font-bold m-5" v-on:click="setExample">Get an example passage</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ContentSubmit',
  methods: {
    sendRequest: function () {
      const input = this.$parent.inputText;

      const endpoint = "https://studyguide-backend-nwitjszpka-ue.a.run.app/";
      // const endpoint = "http://localhost:8080/";

      const jsonBody = { text: input };
      const stringed = JSON.stringify(jsonBody);

      fetch(endpoint, {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: stringed,
      })
      .then(response => response.json())
      .then(data => {
        console.log('Success:', data);

        let tempFlashcards = data.flashcards;

        for (let i = 0; i < tempFlashcards.length; i++) {
          let blankSize = tempFlashcards[i].answer.length;
          let blankSpot = "{" + blankSize + "}";

          let blanks = "";
          for (let j = 0; j < blankSize; j++) {
            blanks = blanks + "_";
          }

          tempFlashcards[i].question = tempFlashcards[i].question.replace(blankSpot, blanks);
        }

        this.$parent.flashcards = tempFlashcards;
      })
      .catch((error) => {
        console.error('Error:', error);
      });
    },
    setExample: function () {
      this.$parent.inputText = "Microsoft Corporation (/ˈmaɪkroʊsɒft/ MY-kroh-soft) is an American multinational technology company with headquarters in Redmond, Washington. It develops, manufactures, licenses, supports, and sells computer software, consumer electronics, personal computers, and related services. Its best known software products are the Microsoft Windows line of operating systems, the Microsoft Office suite, and the Internet Explorer and Edge web browsers. Its flagship hardware products are the Xbox video game consoles and the Microsoft Surface lineup of touchscreen personal computers. Microsoft ranked No. 21 in the 2020 Fortune 500 rankings of the largest United States corporations by total revenue;[3] it was the world's largest software maker by revenue as of 2016[4] and is considered one of the domestic Big Five technology companies.";
    }
  }
}
</script>
