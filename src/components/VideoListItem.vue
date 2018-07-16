<template> 
    <li class="list-group-item " @click="onVideoSelect">
        <img class="mr-3" :src="thumbnailsUrl" />
        <div class="media-body">{{ snippteTitle }}</div>       
    </li>    
</template>

<script>
    export default{
        name: 'VideoListItem',
        props: ['video'],
        methods: {
            onVideoSelect(){
                this.$emit('videoSelect', this.video);
            }
        },
        computed: {
            thumbnailsUrl() {
                return this.video.snippet.thumbnails.default.url;
            },
            snippteTitle() {
                return this.video.snippet.title
            }
        },
        
    }
</script>

<style scoped>
    li {
        display: flex;
        cursor: pointer;
    }

    li:hover {
        background-color: #eee;
    }
</style>
