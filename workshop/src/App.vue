/* eslint-disable no-unused-vars */
/* eslint-disable no-unused-vars */
/* eslint-disable no-unused-vars */
<template>
  <div>
<SearchBar @termChange="onTermChange"></SearchBar>
<VideoList></VideoList>
  </div>  
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';


const API_KEY = 'AIzaSyAYY8ihb_BoBVvWwB0TxoUmWKP7dBFy7zs';
export default {
components: { SearchBar,
VideoList },
name: 'App',
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
        }).then(response => console.log(response));
    }
}
};
</script>
