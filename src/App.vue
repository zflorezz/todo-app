<script setup>  
import {ref} from 'vue'

const name = ref('')
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

    </section>

    <section class="todo-list">

    </section>
  </main>
</template>