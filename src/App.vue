<template>
    <div class="container">
        <div>
            <SearchBar @searchTermChange="onSearchTermChange">
            </SearchBar>
            <div class="row">
                <VideoDetail :video="selectedVideo" />
                <VideoList :listOfVideos="videos" 
                @videoSelected="onVideoSelected">
                </VideoList>
            </div>
        </div>
    </div>
</template>
<script>

import axios from "axios";
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
import VideoDetail from "./components/VideoDetail"

const API_KEY = "AIzaSyAJmp04p6T1ocCyyo1B28lf5_NZhoSrgQk";
const SEARCH_URL = "https://www.googleapis.com/youtube/v3/search";

export default {
    /* eslint-disable */
    name : "YouTube",
    components : {
        SearchBar : SearchBar,
        VideoList : VideoList,
        VideoDetail
    },
    data : function()
    {
        return {
            videos : [],
            selectedVideo : null
        };
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
            } ).then( response => {
                this.videos = response.data.items;
            } );
        },
        /**
         * 
         */
        onVideoSelected : function( selectedVideo )
        {
            this.selectedVideo = selectedVideo;
        }
    }
}
</script>
