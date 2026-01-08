<!-- <script setup lang="ts">
import { ref } from 'vue';


const todos = defineModel('todos');
const newTitle = ref('');
const nextId = ref(Math.max(0, ...todos.value.map(t => t.id)) + 1);

function addTodo() {
  const title = newTitle.value;
  todos.value.push({ id: nextId.value++, text: title, completed: false });
  newTitle.value = '';
} 

</script>



<template>
    <section>
      <h2>New Todo</h2>
      <div style="display: flex; align-items: center; gap:0.5rem; margin: 0.25rem 0;">
        <input 
          v-model="newTitle" 
          placeholder="New todo title"
          aria-label="New todo title"
        />
        <button v-on:click="addTodo" :disabled="!newTitle">Add</button>
      </div>
    </section>
</template> -->




<script setup lang="ts">
import AddTodo from './components/AddTodo.vue';
import {useTodoStore} from '../stores/todoStore';
import { ref } from 'vue';

const todoStore = useTodoStore();

const newTitle = ref<string>('');

</script>


<template>
    <section>
      <h2>New Todo</h2>
      <div style="display: flex; align-items: center; gap:0.5rem; margin: 0.25rem 0;">
        <input
          type ="text"
          v-model="newTitle" 
          placeholder="New todo title"
          aria-label="New todo title"
        />
        <button v-on:click="todoStore.addTodo(newTitle)" :disabled="!newTitle">Add</button>
      </div>
    </section>
</template>