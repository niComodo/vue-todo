<template>
    <div>
        <h2>{{ titolo }}</h2>

        <!--aggiungi nuovo todo-->
        <AddTodo @createTodo="add"/>

        <!--statistiche todo-->
        <TodoCounter :todoList="todoList"/>

        <!--lista todo-->
        <div class="todo-list">
            <TodoItem v-for="(item, key) in todoList" v-bind:key="key" :item="item" @removeTodo="remove(key)"/>
        </div>
    </div>
</template>

<script>
import AddTodo from './AddTodo.vue'
import TodoItem from './TodoItem.vue'
import TodoCounter from './TodoCounter.vue'

export default {
    name: 'Todo',
    data() {
        return {
            titolo: 'Todo List',
            todoList: [],
        }
    },
    props: {
        newTodoContent: String
    },
    components: {
        AddTodo,
        TodoItem,
        TodoCounter,
    },
    methods: {
        add(todo) {
            this.todoList.push(todo)
        },
        remove(key) {
            this.todoList.splice(key, 1)
        }
    },
}
</script>

<style scoped>
#todo {
    text-align: center;
}

.todo-list {
    list-style-type: none;
}
</style>
