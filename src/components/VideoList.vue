<template>
  <div id="videolist">
    <ul>
      <app-video-list-item
        v-for="video in videos"
        :video="video"
        :key="video.etag"
      ></app-video-list-item>
    </ul>
  </div>
</template>

<script>
import VideoListItem from "@/components/VideoListItem.vue";

export default {
  name: "VideoList",
  components: {
    appVideoListItem: VideoListItem,
  },
  props: {
    videos: {
      type: Array,
      required: false,
    },
  },
};
</script>

<style scoped>
</style>