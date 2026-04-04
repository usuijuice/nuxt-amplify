<template>
  <div class="todo-app">
    <h1>TODOアプリ</h1>

    <div class="input-section">
      <input
        v-model="newTodo"
        @keyup.enter="addTodo"
        placeholder="新しいタスクを入力..."
        class="todo-input"
      />
      <button @click="addTodo" class="add-button">追加</button>
    </div>

    <ul class="todo-list">
      <li v-for="todo in todos" :key="todo.id" class="todo-item">
        <input
          type="checkbox"
          v-model="todo.completed"
          class="checkbox"
        />
        <span :class="{ completed: todo.completed }" class="todo-text">
          {{ todo.text }}
        </span>
        <button @click="deleteTodo(todo.id)" class="delete-button">削除</button>
      </li>
    </ul>

    <div v-if="todos.length === 0" class="empty-state">
      タスクがありません
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

interface Todo {
  id: number
  text: string
  completed: boolean
}

const newTodo = ref('')
const todos = ref<Todo[]>([])
let nextId = 1

const addTodo = () => {
  if (newTodo.value.trim()) {
    todos.value.push({
      id: nextId++,
      text: newTodo.value.trim(),
      completed: false
    })
    newTodo.value = ''
  }
}

const deleteTodo = (id: number) => {
  todos.value = todos.value.filter(todo => todo.id !== id)
}
</script>

<style scoped>
.todo-app {
  max-width: 600px;
  margin: 50px auto;
  padding: 20px;
  font-family: Arial, sans-serif;
}

h1 {
  text-align: center;
  color: #333;
}

.input-section {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

.todo-input {
  flex: 1;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-size: 16px;
}

.add-button {
  padding: 10px 20px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 16px;
}

.add-button:hover {
  background-color: #45a049;
}

.todo-list {
  list-style: none;
  padding: 0;
}

.todo-item {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
  margin-bottom: 10px;
  background-color: #f9f9f9;
}

.checkbox {
  width: 20px;
  height: 20px;
  cursor: pointer;
}

.todo-text {
  flex: 1;
  font-size: 16px;
}

.todo-text.completed {
  text-decoration: line-through;
  color: #999;
}

.delete-button {
  padding: 5px 15px;
  background-color: #f44336;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.delete-button:hover {
  background-color: #da190b;
}

.empty-state {
  text-align: center;
  color: #999;
  padding: 20px;
  font-size: 16px;
}
</style>
