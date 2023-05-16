<template>
<div class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <VideoList  :videos="videos"></VideoList>
</div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar.vue';
import VideoList from './components/VideoList.vue';
const API_KEY='AIzaSyDWNuyiz-a-dyDTZuaMhyyc9nWUR2SBfmU';
export default{
    name: "App",
    components: {
         SearchBar,
         VideoList
         },
         data(){
            return{videos:[]};
         },
         methods:{
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
