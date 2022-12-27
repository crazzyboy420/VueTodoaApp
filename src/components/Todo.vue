<template>
    <ul class="my-4 ">
       <TodoItem v-for="todo in todos" @completed-todo="$emit('completed-todo',todo.id)" @delete-todo="$emit('delete-todo',todo.id)" :key="todo.id" :todo="todo" />
    </ul>
</template>

<script>
import TodoItem from './TodoItem.vue';
export default {
    name:'Todo',
    components:{
        TodoItem
    },
    props:{
        todos:Array
    },
    emits:['delete-todo','completed-todo']
}
</script>