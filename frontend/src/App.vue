<!-- <script setup lang="ts">
import {ref, computed} from 'vue';
import AddTodo from './components/AddTodo.vue';

const name = ref("Vue 3 with TypeScript");
type Todo = { id: number; text: string; completed: boolean};

const todos = ref<Todo[]>([
  { id: 1, text: "Buy groceries", completed: false },
  { id: 2, text: "Write report", completed: true },
  { id: 3, text: "Call Alice", completed: false },
]);

const completedTodos = computed(
  function completedTodos(): number {
    const comp = todos.value.filter( todo => !todo.completed );
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
          style="display: flex; align-items: center; gap:0.5rem; margin: 0.25rem 0;"
        >
          <input type="checkbox" v-model="todo.completed" />
          <span :style="{ textDecoration: todo.completed ? 'line-through' : 'none' }">
            {{ todo.text }}
          </span>
        </li>
      </ul>

      <p type="text">
        todos: {{completedTodos}}
      </p>

    </section>


    <AddTodo v-model:todos="todos" />

  </div>
  </template> -->






<script setup lang="ts">
import AddTodo from './components/AddTodo.vue';
import { useTodoStore } from './stores/todoStore'; //storeのインポート

const todoStore = useTodoStore(); //storeの使用
</script>


<template>
  <div id="app">    
    <section class="todo-app">
      <h2>Todos</h2>
      <ul>
        <li
          v-for="todo in todoStore.todos"
          :key="todo.id"
          style="display: flex; align-items: center; gap:0.5rem; margin: 0.25rem 0;"
        >
          <input type="checkbox" v-model="todo.completed" />
          <span :style="{ textDecoration: todo.completed ? 'line-through' : 'none' }">
            {{ todo.title }}
          </span>
          <button @click="todoStore.removeTodo(todo.id)">Remove</button>
        </li>
      </ul>
    </section>

    <AddTodo />
  </div>
</template>