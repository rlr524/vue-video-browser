<template>
  <div>
    <li>{{ video.snippet.title }}</li>
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
};
</script>

<style scoped>
</style>