<template>
  <!-- We're using v-if here in much the same way we'd use guard in Swift, e.g. guarding against the
component loading if the video object is null  -->
  <div id="videodetail" class="col-md-8" v-if="video">
    <div class="details embed-responsive embed-responsive-16by9">
      <iframe
        class="embed-responsive-item"
        :src="videoSource"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
      ></iframe>
      <h4>{{ video.snippet.title }}</h4>
      <p>{{ video.snippet.description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "VideoDetail",
  props: {
    video: {
      type: Object,
      required: false,
    },
  },
  computed: {
    videoSource() {
      // Using some ES6 syntax to destructure videoId...since it's the property of this.video.id, we can name the const videoId and leave off the property
      const { videoId } = this.video.id;
      return `https://www.youtube.com/embed/${videoId}`;
    },
  },
};
</script>

<style scoped>
.details {
  margin-top: 0.625 em;
  padding: 0.625em;
  border: 1px #ddd solid;
  border-radius: 0.25em;
}
</style>