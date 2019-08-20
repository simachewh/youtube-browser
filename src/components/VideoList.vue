<template>
        <ul class="list-group col-md-4">
            <VideoListItem 
            v-for="currentVideo in listOfVideos" 
            :video="currentVideo" 
            :key="currentVideo.etag"
            @videoSelected="onVideoSelected">
            </VideoListItem>
        </ul>
</template>

<script>
/* eslint-disable */
import VideoListItem from "./VideoListItem";
export default {
    name : "VideoList",
    components : {
        VideoListItem
    },
    props : {
        listOfVideos : Array
    },
    methods : {
        onVideoSelected : function( selectedVideo )
        {
            this.$emit( "videoSelected", selectedVideo )
        }
    }
    }
    
</script>

<style>

</style>
