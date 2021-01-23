<template>
  <div id="app" class="container">
    <app-search-bar @searchTermChange="onTermChange"></app-search-bar>
    <div class="row">
      <app-video-detail :video="selectedVideo"></app-video-detail>
      <app-video-list
        :videos="videosArr"
        @videoSelect="onVideoSelectApp"
      ></app-video-list>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "@/components/SearchBar.vue";
import VideoList from "@/components/VideoList.vue";
import VideoDetail from "@/components/VideoDetail.vue";
const apiKey = process.env.VUE_APP_API_KEY;

export default {
  name: "App",
  components: {
    appSearchBar: SearchBar,
    appVideoList: VideoList,
    appVideoDetail: VideoDetail,
  },
  data() {
    return {
      videosArr: [],
      selectedVideo: null,
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
            maxResults: 5,
            q: searchTerm,
          },
        })
        .then((res) => {
          this.videosArr = res.data.items;
        });
    },
    onVideoSelectApp(video) {
      this.selectedVideo = video;
    },
  },
};
</script>

<style>
</style>
