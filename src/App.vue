

<template>
  <div class="flex justify-center items-center min-h-screen bg-[#cbd7e3]">
    <div class="h-auto  w-96 bg-white rounded-lg p-4">
       <div class="flex justify-between items-center mb-4">
        <h1 class="text-3xl mb-4 font-semibold mt-2 text-[#063c76]">Todo List</h1>
         <button @click="completeAll" class="bg-gray-500 text-white py-2 px-4 rounded">Complete all</button>
       </div>
       <TodoForm :editText="edittext" @addTodo="addTodo" />
       <Todo @edit-todo="editTodo" :todos="todos" @completed-todo="handleChange" @delete-todo="handleClick" />

       <div class="flex justify-between items-center mt-4">
        <p class="text-gray-400 text-sm">{{ taskCount <= 1? `${taskCount} Task`: `${taskCount} Tasks`}} </p>
        <button @click="clearAll" class="text-white bg-red-400 text-sm py-1 px-2 rounded">Clear</button>
       </div>
    </div>
</div>
</template>
<script>
import TodoForm from './components/TodoForm.vue';
import Todo from './components/Todo.vue';
import { computed } from '@vue/runtime-core';

export default{
  name:"Todo App",
  components:{
    TodoForm,Todo
  },
  data(){
    return{
      todos:[],
      edittext:{},
    }
  },
  methods:{
    handleClick(id){
       this.todos = this.todos.filter(todo=>todo.id != id);
    },
    handleChange(id){
      this.todos = this.todos.map((todo)=>todo.id==id ? {...todo,completed:!todo.completed}:todo);
    },
    addTodo(todo){
      this.todos = [{id: Math.floor(Math.random() * 10000),todo:todo,completed:false},...this.todos]
      console.log(this.todos);
    },
    clearAll(){
      this.todos = this.todos.filter(todo=>todo.completed == false);
    },
    completeAll(){
       this.todos = this.todos.map(todo=> {
        return {...todo,completed:true}
       })
    },
    editTodo(id){
        let editval = this.todos.filter(todo=>todo.id == id);
        this.edittext = editval[0];
    }
  },
  created(){
   this.todos = [
        {id:1,todo:"Hit the gym",completed:false},
        {id:2,todo:"Pay bills",completed:true},
        {id:3,todo:"Meet George",completed:false},
    ]
  },
  computed:{
    taskCount(){
      return this.todos.filter(todo=>todo.completed == false).length;
    }
  }

}
</script>
<style scoped>

</style>
