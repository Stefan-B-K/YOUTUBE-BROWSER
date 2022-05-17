<template>
  <div class="container"> 
    <SearchBar @inputChange="onInputChange"></SearchBar>
    <div class="row">
      <VideoDetail v-if="clickedVideo" :video="clickedVideo"></VideoDetail>
      <VideoList :videos="videos" @videoClick="onVideoClick"></VideoList>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import SearchBar from './components/SearchBar'
import VideoList from './components/VideoList'
import VideoDetail from './components/VideoDetail'
import { API_KEY } from './private'

export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data() {
    return {
      videos: [],
      clickedVideo: null
    };
  },
  methods: {
    onInputChange(searchInput) {
      axios
        .get('https://www.googleapis.com/youtube/v3/search', {
          params: {
            key: API_KEY,
            type: 'video',
            part: 'snippet',
            q: searchInput,
          },
        })
        .then(response => this.videos = response.data.items)
        .catch(error => console.log(error))
    },
    onVideoClick(video) {
      this.clickedVideo = video
    }
  },
}
</script>