
<template>
  <div>
<SearchBar @termChange="onTermChange"></SearchBar>
<VideoList :videos="videos"></VideoList>
  </div>  
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';


const API_KEY = 'AIzaSyAG3UuIUZFf3vtZbg6QZQM4DkE6pTIO9UM';
export default {
name: 'App',
components: { SearchBar,
VideoList },
data(){
  return {  
      videos: []
  };
},
methods:{
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
