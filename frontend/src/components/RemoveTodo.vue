<!-- <script setup lang="ts">
import AddTodo from './components/AddTodo.vue';
import {useTodoStore} from '../stores/todoStore';

const todoStore = useTodoStore();
</script>


<template>
    <section>
      <h2>New Todo</h2>
      <div style="display: flex; align-items: center; gap:0.5rem; margin: 0.25rem 0;">
        <input 
          v-model="id" 
          placeholder="Todo ID to remove"
          aria-label="Todo ID to remove"
        />
        <button v-on:click="todoStore.removeTodo(id)" :disabled="!id">Remove</button>
      </div>
    </section>
</template> -->