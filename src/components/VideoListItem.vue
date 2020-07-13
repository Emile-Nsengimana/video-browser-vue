<template>
  <div class="list-group-item">
    <div class="media">
      <img :src="thumbnailsUrl" alt="..." />
      <li class="media-body" @click="videoSelected">
        <h6>{{ video.snippet.title}}</h6>
      </li>
    </div>
  </div>
</template>

<script>
export default {
  name: "VideoListItem",
  props: ["video"],
  computed: {
    thumbnailsUrl() {
      return this.video.snippet.thumbnails.default.url;
    }
  },
  methods: {
    videoSelected() {
      this.$emit("videoSelected", this.video);
    }
  }
};
</script>

<style scoped>
.list-group-item:hover {
  background: #ddd;
  cursor: pointer;
}
</style>
