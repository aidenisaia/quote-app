<template>
  <div class="home">
    <!-- <h2 v-for="quote in quotes" v-bind:key="quote.id">
      <p>"{{ quote.quote }}"</p>
      <p>{{ quote.source }}</p>
      <p>{{ quote.context }}</p>
      <hr />
    </h2> -->
    <button v-on:click="sortByGame">Quotes by game</button>
  </div>
</template>
<style></style>
<script>
import axios from "axios";
export default {
  data: function () {
    return {
      quotes: [],
      gamequotes: [],
      moviequotes: [],
    };
  },
  created: function () {
    axios
      .get("https://gist.githubusercontent.com/benchprep/dffc3bffa9704626aa8832a3b4de5b27/raw/quotes.json")
      .then((response) => {
        console.log(response.data);
        this.quotes = response.data;
      });
  },
  methods: {
    sortByGame: function (array) {
      array.forEach(function (quote) {
        if (quote["theme"] == "games") {
          this.gamequotes.push(quote);
        }
      });
    },
  },
};
</script>
