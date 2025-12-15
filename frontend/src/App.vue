<script setup lang="ts">
import {ref, computed} from 'vue';

const name = ref("Vue 3 with TypeScript");
type Todo = { id: number; text: string; completed: boolean};

const todos = ref<Todo[]>([
  { id: 1, text: "Buy groceries", completed: false },
  { id: 2, text: "Write report", completed: true },
  { id: 3, text: "Call Alice", completed: false },
]);

const completedTodos = computed(
  function completedTodos(): number {
    const comp = todos.value.filter( completed => false );
    return comp.length;
  })
</script>


<template>
  <div id="app">
    
    <section class="todo-app">
      <h2>Todo List</h2>

      <ul>
        <li
          v-for="todo in todos"
          :key="todo.id"
          style="diisplay: flex; align-items: center; gap:0.5rem; margin: 0.25rem 0;"
        >
          <input type="checkbox" v-model="todo.completed" />
          <span :class="{ completed: todo.completed }">
            {{ todo.title }}
          </span>
        </li>
      </ul>

      <p type="text" v-model="comp">
        todos: {{completedTodos}}
      </p>

    </section>
  </div>
</template>