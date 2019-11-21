<template>
    <div>
        <h1>유튜브 검색기</h1>
        <input @change="onInput" type="text" class="my-3"> <!-- v-on change : input 이벤트가 변할때마다 밑에 methods--> 
        <!-- 검색 데이터를 상위 Component인 App에 올려주고, App은 youtube
        open api에 데이터를 주고 해당 정보를 받아오는 형식이다. -->
    </div>
</template>

<script>


export default {
    name: 'SearchBar',
    methods: {
        onInput(event) {
            console.log('==SearchBar==') // 그냥 편하게 보려고!
            console.log(event.target.value) // 이게 변경될 때마다 부모 컴포넌트에 해당 정보를 보내주고 싶어
            // 부모 -> 자식 : prompts, 자식 -> 부모 : event를 발생
            this.$emit('input-change-event', event.target.value)
            // this.$emit(이벤트 이름(임의로), 값) : 커스텀 이벤트 발생
            // 이벤트 이름의 이벤트를 발생 시킴(트리거)
        }
    }
}
</script>

<style>

</style>