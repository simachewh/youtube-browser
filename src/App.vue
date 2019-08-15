<template>
    <div>
        <div>Sup!</div>
        <div>
            <SearchBar @searchTermChange="onSearchTermChange"></SearchBar>
            <VideoList></VideoList>
        </div>
    </div>
</template>
<script>

import axios from "axios";
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
const API_KEY = "AIzaSyAJmp04p6T1ocCyyo1B28lf5_NZhoSrgQk";
const SEARCH_URL = "https://www.googleapis.com/youtube/v3/search";

export default {
    /* eslint-disable */
    name : "YouTube",
    data : {
        videos : ""
    },
    components : {
        SearchBar : SearchBar,
        VideoList : VideoList
    },
    methods : {
        onSearchTermChange : function( searchTerm )
        {
            axios.get( SEARCH_URL, {
                params : {
                    key : API_KEY,
                    type : "video",
                    part : "snippet",
                    q : searchTerm
                }
            } ).then( function( response ){
                this.$emit(  )
            } );
        }
    }
}
</script>
