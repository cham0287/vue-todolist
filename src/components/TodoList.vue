<script setup lang="ts">
import { ref } from 'vue';

type Todo = {
  id: number;
  text: string;
  completed: boolean;
};

const todos = ref<Todo[]>([
  { id: 1, text: '우유 사기', completed: false },
  { id: 2, text: '운동하기', completed: true },
  { id: 3, text: '코딩 공부하기', completed: false },
  { id: 4, text: '책 읽기', completed: false },
]);

const toggleTodo = (todo: Todo) => {
  todo.completed = !todo.completed;
};
</script>

<template>
  <h1>Vue TodoList</h1>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      <input
        type="checkbox"
        :checked="todo.completed"
        @change="toggleTodo(todo)"
      />
      <span :class="{ completed: todo.completed }">{{ todo.text }}</span>
    </li>
  </ul>
</template>

<style scoped>
.completed {
  text-decoration: line-through;
  color: #888;
}
</style>
