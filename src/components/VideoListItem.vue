<template>
  <li class="list-group-item media" @click="onVideoClick">
    <img class="mr-3" :src="thumbnailURL" />
    <div class="media-body">
      {{ video.snippet.title }}
    </div>
  </li>
</template>

<script>
export default {
  name: "VideoListItem",
  props: {
    video: Object
  },
  computed: {
    thumbnailURL() {
      return this.video.snippet.thumbnails.default.url;
    }
  },
  methods: {
    onVideoClick() {
      this.$emit('videoClick', this.video)
    }
  }
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
.media-body {
  margin-left: 15px;
}
</style>
