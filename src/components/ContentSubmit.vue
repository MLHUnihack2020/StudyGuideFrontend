<template>
  <div class="">
    <p class="my-5 text-lg">Paste in your text that you want to study below:</p>

    <div>
      <textarea class="shadow-lg p-5 rounded-lg" id="inputText" name="inputText" rows="10" cols="70" v-model="$parent.inputText"></textarea>
    </div>
    <div>
      <button class="text-lg shadow-md px-3 py-2 rounded-lg font-bold m-10" v-on:click="sendRequest">Submit</button>
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
        this.$parent.flashcards = data.flashcards
      })
      .catch((error) => {
        console.error('Error:', error);
      });
    }
  }
}
</script>
