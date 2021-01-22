<template>
  <div id="app">
    <app-search-bar @searchTermChange="onTermChange"></app-search-bar>
    <app-video-list></app-video-list>
    {{ videos.length }}
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "@/components/SearchBar.vue";
import VideoList from "@/components/VideoList.vue";
const apiKey = process.env.VUE_APP_API_KEY;

export default {
  name: "App",
  components: {
    appSearchBar: SearchBar,
    appVideoList: VideoList,
  },
  data() {
    return {
      videos: [],
    };
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
        .then((res) => {
          this.videos = res.data.items;
        });
    },
  },
};
</script>

<style>
</style>
