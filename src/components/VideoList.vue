<template>
  <ul class="list-group col-md-4">
    <VideoListItem
      v-for="video in videos"
      :key="video.etag"
      :video="video"
      @videoClick="onVideoClick"
    >
    </VideoListItem>
  </ul>
</template>

<script>
import VideoListItem from "./VideoListItem";

export default {
  name: "VideoList",
  props: {
    videos: Array, // or just ['videos'] without validation
  },
  components: {
    VideoListItem,
  },
  methods: {
    onVideoClick(video) {
      this.$emit('videoClick', video)
    }
  }
};
</script>

<style></style>
