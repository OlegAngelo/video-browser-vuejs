<template>
    <div>
        <SearchBar @termChange="onTermChange"></SearchBar>
        <div class="row">
            <VideoDetail :video="selectedVideo"> </VideoDetail>
            <VideoList @videoSelect="onVideoSelect" :videos="videos"></VideoList>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail'

const API_KEY ='AIzaSyBsROP9IwN_lpLe-k2JXXjrIfzVuv-Glj0';

export default {
    name: 'App',
    components:{
        SearchBar,
        VideoList,
        VideoDetail
    },
    data() {
        return{
            videos: [],
            selectedVideo: null
        };
    },
    methods: {
        onTermChange(searchTerm){
            axios.get('https://www.googleapis.com/youtube/v3/search', {
              params:{
                key: API_KEY,
                type: 'video',
                part: 'snippet',
                query: searchTerm
              }  
            })
            .then(response => {
                this.videos = response.data.items
            });
        },
        onVideoSelect(video){
            this.selectedVideo = video;
        }
    }
}
</script>

<style>

</style>
 