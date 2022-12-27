<template>
    <li class=" mt-4">
        <div class="flex gap-2">
            <div class="w-9/12 h-12 bg-[#e0ebff] rounded-[7px] flex justify-start items-center px-3">
                <span @click="$emit('completed-todo',todo.id)" :class="[todo.completed ? 'bg-green-500 text-white':' text-gray-400',' w-7 h-7 bg-white rounded-full border border-white transition-all cursor-pointer hover:border-[#36d344] flex justify-center items-center']">
                    <font-awesome-icon icon="fa-solid fa-check" />
                </span>
                <span id="strike1" :class="[{'line-through':todo.completed},'text-sm ml-4 text-[#5b7a9d] font-semibold']">{{ todo.todo }}</span>
            </div>
            <span @click="handleClick(todo.id)"  class="w-1/4 h-12 cursor-pointer bg-[#e0ebff] text-red-400 text-xl rounded-[7px] flex justify-center font-semibold items-center ">
                <font-awesome-icon icon="fa-solid fa-trash" />
            </span>
        </div>
    </li>
</template>

<script>
export default {
    name:'TodoItem',
    props:{
        todo:Object
    },
    methods: {
        handleClick(id){
          this.$emit('delete-todo', id)
        } 
    },
}
</script>