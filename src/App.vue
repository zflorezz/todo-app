<script setup>  
import {ref} from 'vue'
const todos = ref([])
const name = ref('')
const input_content = ref('')

const addTodo = () => {
  if(input_content.value.trim() === '') {
    return
  }

  todos.value.push({
    content: input_content.value,
  })

 input_content.value = ''
  //console.log(todos)

}

</script>

<template>
  <main class="app">
    <section class="greeting">
      <h2 class="title">
        What's up, <input type="text" placeholder="name" v-model="name" />
        <!-- {{ name }} -->
      </h2>
    </section>

    <section class="create-todo">
      <h3>CREATE A TODO</h3>
      <form @submit.prevent="addTodo">
        <h4>What's on your todo list?</h4>
        <input type="text" placeholder="e.g, Make A Video" v-model="input_content" />
        <!-- {{ input_content }} -->
      </form>
    </section>

    <section class="todo-list">

    </section>
  </main>
</template>