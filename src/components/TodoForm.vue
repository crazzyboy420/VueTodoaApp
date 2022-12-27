<template>
    <form @submit="addTodo" class="flex items-center bg-gray-100 px-4 py-4 rounded-md">
        <img src="https://i.ibb.co/4S0t2ps/download.png" class="w-6 h-6" alt="Add todo">
        <input type="text" v-model="text" placeholder="Type your todo" class="w-full text-lg px-4 py-1 border-none outline-none bg-gray-100 text-gray-500">
        <button type="submit" class="appearance-none w-8 h-8 bg-[url('https://i.ibb.co/Q6DXPGf/plus-132696644e79a1f05c3b.png')] bg-no-repeat bg-contain"></button>
    </form>
</template>

<script>
export default {
  name:"TodoForm",
  data() {
    return {
      text: ""
    }
  },
  methods:{
    addTodo(e){
      e.preventDefault();

      if(!this.text){
        return alert("Please type todo")
      }
      this.$emit('addTodo',this.text);
      this.text = "";

    }

  }
}
</script>