<template>
  <div>
      <h2>영상 목록</h2>
      <ul class="list-group">
        <video-list-item 
        v-for="video in videos" 
        :key="video.id.videoId" 
        :video="video" 
        @video-select-event="selectedVideo"> <!-- 반복문에서 나온 
         video 인자를 같이 넘겨줘야함 --> 
        <!-- 
            VideoListItem에서의 props video =반복문 이용해서 나온 video
        -->
        <!-- v-for에서는 key가 필수이다. 반복할 데이터를 컴포넌트로 전달하려면, props도 사용해야한다. 
            key는 객체나 배열처럼, 기본타입이 아닌 값을 사용할 수 없다 -->
        </video-list-item>
        <!-- 부모 컴포넌트에서는 이벤트 listen(v-on) ->원하는 메서드 실행 -->
      </ul>
  </div> <!-- div 두 개 만들 수 없음. template에서는 반드시 하나의 큰 element로 묶고 시작해야한다 -->
</template>

<script>
import VideoListItem from './VideoListItem.vue'
export default {    // 파일 전체를 export
    name: 'VideoList',
    components: {
        VideoListItem
    },
    // props = 부모 컴포넌트 -> 자식 컴포넌트로 데이터를 전달할 때 사용 ( 자식 컴포넌트에 작성한다. )
    // 이 props에 등록된 데이터들은 자식 컴포넌트에서 data처럼 접근할 수 있다.
    props: {
        videos: {
            type: Array,
            required: true
        }
    },
    methods: {
        selectedVideo(video) {
            this.$emit('video-select-event', video)
        }
    }
}
</script>

<style>

</style>