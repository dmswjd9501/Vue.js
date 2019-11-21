<template>
    <li @click="seletedVideo" class="list-group-item my-3 py-3">
        <img :src="video.snippet.thumbnails.high.url" :alt="video.snippet.title">
        <h3>{{ video.snippet.title }}</h3>
        <p>{{ video.snippet.description }}</p>
    </li>
</template>

<script>
export default {
    name: 'VideoListItem',
    props: {
        video: {    // video가 넘어올건데
            type: Object,   // type은 object일거야
            required: true
        }
    },
    methods: {
        selectedVideo() {
            // video-select-event $emit
            // 자식 컴포넌트에서는 이벤트 발생 (값 전달)
            this.$emit('video-select-event', this.video) // 트리거 : 이벤트를 발생한다 -> 리스트로 가보자
            
        }
    }
}
</script>

<style>
/* scoped: 해당 컴포넌트에서만 사용되는 style */
img {
    width: 360px;
}
li {
    cursor: pointer;
}
li:hover {
    background-color: lightblue;
}
</style>