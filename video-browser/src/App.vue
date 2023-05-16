<template>
<div>
    <SearchBar @termChange="onTermChange"></SearchBar>
</div>
</template>

<script>
import SearchBar from './components/SearchBar.vue';
const API_KEY='AIzaSyDqe3Tmf7_GaFbzptjUJq42hp0q24cDtKc';
export default{
    name: "App",
    components: {
         SearchBar
         },
         methods:{
            onTermChange: function(searchedTerm){
                console.log(searchedTerm);

            }
         }
};
</script>
