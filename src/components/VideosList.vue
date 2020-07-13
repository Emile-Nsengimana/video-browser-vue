<template>
  <ul class="list-group col-md-4">
    <VideoListItem
      v-for="video in videos"
      :video="video"
      :key="video.etag"
      @videoSelected="onSelectVideo"
    ></VideoListItem>
  </ul>
</template>

<script>
import VideoListItem from "./VideoListItem";

export default {
  name: "VideosList",
  components: {
    VideoListItem
  },
  props: {
    videos: Array
  },
  methods: {
    onSelectVideo(video) {
      console.log(">>>", video);
      this.$emit("videoSelected", video);
    }
  }
};
</script>

<style></style>
