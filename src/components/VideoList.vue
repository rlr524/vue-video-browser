<template>
  <div class="col-md-4" id="videolist">
    <ul class="list-group">
      <app-video-list-item
        v-for="video in videos"
        :video="video"
        :key="video.etag"
        @videoSelect="onVideoSelectVideoList"
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
  methods: {
    onVideoSelectVideoList(video) {
      this.$emit("videoSelect", video);
    },
  },
};
</script>

<style scoped>
</style>