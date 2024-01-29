<script setup>  
import {ref} from 'vue'
const todos = ref([])
const name = ref('')
const input_content = ref('')
const input_category = ref(null)

const addTodo = () => {
  if(input_content.value.trim() === '' || input_category.value == null) {
    return
  }

  todos.value.push({
    content: input_content.value,
    category: input_category.value,
    done: false,
  })

 input_content.value = ''
 input_category.value = null
 
  //console.log(todos)

}

const removeTodo = (todo) => {
  todos.value = todos.value.filter(t => t !== todo)
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

        <h4>Pick a category</h4>
        <div class="options">
          <label>
            <input type="radio" name="category" value="business" v-model="input_category" />
            <span class="bubble business"></span>
            <div>business</div>
          </label>

          <label>
            <input type="radio" name="category" value="personal" v-model="input_category" />
            <span class="bubble personal"></span>
            <div>Personal</div>
          </label>

          <!-- {{ input_category }} -->
        </div>

        <input type="submit" value="Add Todo" />

      </form>
    </section>

    <section class="todo-list">
      <div class="list">
        <div v-for="todo in todos" :class="`todo-item ${todo.done ? `done` : `not-done`}`" :key="todo">
        <label>
          <input type="checkbox" v-model="todo.done" />
          <span :class="`bubble ${todo.category}`"></span>
        </label>
        <div class="todo-content">
          <input type="text" v-model="todo.content" />
        </div>
        <div class="actions">
          <button class="delete" @click="removeTodo(todo)">Delete</button>
        </div>
        </div>
      </div>
    </section>
  </main>
</template>