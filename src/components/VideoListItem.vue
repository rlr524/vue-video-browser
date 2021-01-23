<template>
  <div id="videolistitem">
    <li class="list-group-item media" @click="onVideoSelectVideoListItem">
      <img class="mr-3" :src="thumbnailUrl" />
      <div class="media-body">
        {{ video.snippet.title }}
      </div>
    </li>
  </div>
</template>

<script>
export default {
  name: "VideoListItem",
  props: {
    video: {
      type: Object,
      required: false,
    },
  },
  computed: {
    thumbnailUrl() {
      return this.video.snippet.thumbnails.default.url;
    },
  },
  methods: {
    onVideoSelectVideoListItem() {
      this.$emit("videoSelect", this.video);
    },
  },
};
</script>

<style scoped>
li {
  display: flex;
  cursor: pointer;
}
li:hover {
  background-color: #eee;
}
</style>