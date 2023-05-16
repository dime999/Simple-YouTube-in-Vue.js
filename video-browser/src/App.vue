<template>
<div>
    <SearchBar @termChange="onTermChange"></SearchBar>
</div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar.vue';
const API_KEY='AIzaSyDqe3Tmf7_GaFbzptjUJq42hp0q24cDtKc';
export default{
    name: "App",
    components: {
         SearchBar
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
                }).then(response=> console.log(response));

            }
         }
};
</script>
