<template>
    <div>
    <h1>이게 싱글파일 컴포넌트, 최상위 컴포넌트입니다.</h1>
    <!-- 3. 컴포넌트를 호출 -->
    <TodoList category="취업"></TodoList>
    <TodoList category="수업"></TodoList>
    <TodoList category="개인"></TodoList>
    </div>
</template>


<script>
// 1. 컴포넌트를 부모 컴포넌트에서 불러옴.
import TodoList from './components/TodoList.vue'

export default {
    components: {
        TodoList    // 2. 컴포넌트를 추가
    }
}
</script>
<style lang="">
</style>