<template>
    <ul class="list-group media col-md-4">
        <VideoListItem v-for="video in videos" :video="video" :key="video.etag" @videoSelect="onVideoSelect"></VideoListItem>
    </ul>
</template>

<script>
import VideoListItem from './VideoListItem'
    export default{
        name: 'VideoList',
        components:{
            VideoListItem
        },
        props: ['videos'],
        methods: {
            onVideoSelect(video){
                this.$emit('videoSelect', video)
            }
        }
    }
</script>

<style scoped>
    ul {
        margin-top: 20px;
    }
</style>
