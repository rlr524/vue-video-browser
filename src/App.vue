<template>
  <div id="app">
    <app-search-bar @searchTermChange="onTermChange"></app-search-bar>
    <h1>Hello, Madison!</h1>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "@/components/SearchBar.vue";
const apiKey = process.env.VUE_APP_API_KEY;

export default {
  name: "App",
  components: {
    appSearchBar: SearchBar,
  },
  methods: {
    onTermChange(searchTerm) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: apiKey,
            type: "video",
            part: "snippet",
            q: searchTerm,
          },
        })
        .then((res) => console.log(res));
    },
  },
};
</script>

<style>
</style>
