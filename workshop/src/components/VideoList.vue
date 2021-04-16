<template>
    <ul class="list-group col-md-4">
        <VideoListItem
        v-for="video in videos"
        :video="video"
        :key="video.etag"
        @vedioSelect="onVideoSelect"
        >
        </VideoListItem>
    </ul>
</template>


<script>
import VideoListItem from './VideoListItem';

export default {
    name: 'VideoList',
    components: {
        VideoListItem
    },
    props: ['videos'],
    methods: {
        onVideoSelect(video) {
            this.$emit('vedioSelect',video);
        }
    }
};

</script>

<style>

</style>
