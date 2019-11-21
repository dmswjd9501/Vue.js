<template>
  <div id="app">
    <div class="container">
      <search-bar @input-change-event="onInputChange"></search-bar> <!-- 1-3. 출력 -->
    <!-- 자식 컴포넌트 이벤트가 발생되면(이벤트 리스너로 등록) 이 method를 실행시키세요. -->
      <video-detail :video="selectVideo"></video-detail>
      <video-list @video-select-event="selectedVideo" :videos="videos"></video-list>
      
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import SearchBar from './components/SearchBar.vue'
import VideoList from './components/VideoList.vue'
import VideoDetail from './components/VideoDetail.vue'


const API_KEY = process.env.VUE_APP_API_KEY
// 1-1. vue 파일 불러오기

export default {
  name: 'app',
  components: {
    SearchBar, // 1-2. component 등록
    VideoList,
    VideoDetail
  },
  data() {
    return {
      videos: [],
      selectVideo: null   // 저장하기 위해서는 먼저 data
    } // SFC에서는 반드시 data는 함수로 오브젝트를 리턴하도록 작성
      // 참조의 오류가 발생
  },
  methods: {
    selectedVideo(video) {
      console.log('App 도착!')
      this.selectVideo = video
    },
    onInputChange(value) {
      console.log('==App==')
      console.log(value)
      axios.get('https://www.googleapis.com/youtube/v3/search', {
        params: {
          key: API_KEY,
          part: 'snippet',
          type: 'video',
          q: value
        }
      }).then(response => {
        console.log(response)
        // data의 videos에 저장
        this.videos = response.data.items // input 입력된 애들을 가지고 api에서 받아온 데이터를 videos에 저장
      })
      .catch(error => {
        console.log(error) // 에러 자체를 잡을 수 있도록 작성된 것!
      })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
