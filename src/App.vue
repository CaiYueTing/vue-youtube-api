<template>
  <div class="container">
    <SearchBar @termChange = "onTermChange"></SearchBar> 
    <div class="row">
      <VideoDetail :video="selectedVideo"  />
      <VideoList @videoSelect="onVideoSelect" :videos= "videos"></VideoList>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar'
import VideoList from './components/VideoList'
import VideoDetail from './components/VideoDetail'
const youtubeApiKey = 'AIzaSyCJRIPYxIyzBU2stuAeJQdnwCM4Kd6R66I';

export default {
  name: 'app',
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },

  data(){
    return {
      videos: [], selectedVideo: null
    }
  },
  methods: {
    onVideoSelect(video){
      this.selectedVideo = video
      
    },
    onTermChange(searchTerm){
      
      axios.get('https://www.googleapis.com/youtube/v3/search', {
        params:{
          key: youtubeApiKey,
          type: 'video',
          part: 'snippet',
          q: searchTerm
        }
      }).then(res => {
        this.videos = res.data.items
      });

    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
