<template>
<div class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <VideoList @videoSelect="onVideoSelect"  :videos="videos"></VideoList>
    <VideoDetail :video="selectedVideo"></VideoDetail>
</div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar.vue';
import VideoList from './components/VideoList.vue';
import VideoDetail from './components/VideoDetail.vue';
const API_KEY='AIzaSyDWNuyiz-a-dyDTZuaMhyyc9nWUR2SBfmU';
export default{
    name: "App",
    components: {
         SearchBar,
         VideoList,
         VideoDetail
         },
         data(){
            return{videos:[], selectedVideo:null};
         },
         methods:{
            onVideoSelect(video){
               this.selectedVideo = video;
            },
            onTermChange: function(searchedTerm){
                axios.get('https://www.googleapis.com/youtube/v3/search',{
                    params:{
                        key: API_KEY,
                        type:'video',
                        part: 'snippet',
                        q: searchedTerm
                    }
                }).then(response=> {
                    this.videos = response.data.items;
                });

            }
         }
};
</script>
