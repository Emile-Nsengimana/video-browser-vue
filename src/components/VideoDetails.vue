<template>
  <div class="video-details col-md-8" v-if="selectedVideo">
    <iframe
      class="video-frame"
      :src="videoUrl"
      frameborder="0"
      allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
      allowfullscreen
    ></iframe>
    <h2>{{selectedVideo.snippet.title}}</h2>
    <p>{{selectedVideo.snippet.description}}</p>
  </div>
</template>

<script>
export default {
  name: "VideoDetails",
  props: ["selectedVideo"],
  computed: {
    videoUrl() {
      return `https://www.youtube.com/embed/${this.selectedVideo.id.videoId}`;
    }
  }
};
</script>

<style scoped>
.video-details {
  border: 0.5px solid #eee;
}

.video-frame {
  width: 100%;
  height: 385px;
}
</style>
