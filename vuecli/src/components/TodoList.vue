<template>
<div class="todo-list">
    <h2>{{ category }}</h2>
    <input v-model="newTodo" type="text" >
    <button @click="addTodo">추가하기</button>
    <li v-for="todo in todos" :key="todo.id">
    {{ todo.content }}
    <button @click="removeTodo(todo.id)">삭제하기</button>
    <!-- 어떤애를 삭제할 지 모르기때문에 id값을 넘겨주어야 한다. todo object 자체를 넘겨도 되고, todo.id만 넘겨도 ok -->
    </li>
</div>
</template>

<script>
export default {
    props: {
        category: {
            type: String,
            required: true
        }
    },  // 하위컴포넌트로 데이터 전송
    data: function() {
        return{
          newTodo: '',
          todos: []
        }
    },
    methods: {
    addTodo() {
        this.todos.push({
        id: Date.now(),
        content: this.newTodo,
        completed: false
        })
        this.newTodo = ''
    },
    removeTodo(removeTodoId) {
        this.todos = this.todos.filter(todo => {
        return todo.id !== removeTodoId
        }) // 같지않은 애들을 모아서 배열로 만들어서 보낸 것!
    }
    }
}
</script>
<style lang="">
/* li {
    color: skyblue;
} */
</style>