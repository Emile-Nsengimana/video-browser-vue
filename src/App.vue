<template>
  <div class="container">
    <SearchBar @termChange="onTermChange" @search="searchHandler"></SearchBar>
    <div class="row">
      <VideoDetails :selectedVideo="selectedVideo" />
      <VideosList :videos="videos" @videoSelected="onSelectVideo"></VideosList>
    </div>
  </div>
</template>

<script>
import SearchBar from "./components/SearchBar.vue";
import VideosList from "./components/VideosList";
import VideoDetails from "./components/VideoDetails";
import axios from "axios";

const API_KEY = process.env.VUE_APP_API_KEY;

export default {
  name: "App",
  components: {
    SearchBar,
    VideosList,
    VideoDetails
  },
  data() {
    return {
      videos: [],
      searchKey: "",
      selectedVideo: null
    };
  },
  methods: {
    onSelectVideo(video) {
      this.selectedVideo = video;
    },
    onTermChange(searchTerm) {
      this.searchKey = searchTerm;
    },
    async searchHandler() {
      const getVideos = await axios.get(
        "https://www.googleapis.com/youtube/v3/search",
        {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: this.searchKey
          }
        }
      );
      this.videos = getVideos.data.items;
    }
  }
};
</script>
