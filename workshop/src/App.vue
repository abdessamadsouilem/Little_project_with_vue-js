
<template>
  <div class="container">
<SearchBar @termChange="onTermChange"></SearchBar>
<div class="row">
<VideoDetail :video="selectedVideo"></VideoDetail>
<VideoList @vedioSelect="onVideoSelect" :videos="videos"></VideoList>
</div>
  </div>  
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoDetail from './components/VideoDetail';
import VideoList from './components/VideoList';


const API_KEY = 'AIzaSyAG3UuIUZFf3vtZbg6QZQM4DkE6pTIO9UM';
export default {
name: 'App',
components: { SearchBar,
VideoDetail,
VideoList
},
data(){
  return {  
      videos: [] , selectedVideo : null
  };
},
methods:{
   onVideoSelect(video){
    this.selectedVideo = video;
   },
    onTermChange(searchTearm){
        axios
        .get('https://www.googleapis.com/youtube/v3/search', {
            params: {
                key: API_KEY,
                type: 'video',
                part: 'snippet',
                q: searchTearm
            }
        }).then(response => {
            this.videos= response.data.items;
        });
    }
}
};
</script>
