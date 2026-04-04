<template>
  <div class="task-list-page">
    <h1>タスク一覧</h1>

    <div class="navigation">
      <NuxtLink to="/" class="nav-link">ホームに戻る</NuxtLink>
    </div>

    <div class="input-section">
      <input
        v-model="newTask"
        @keyup.enter="addTask"
        placeholder="新しいタスクを入力..."
        class="task-input"
      />
      <button @click="addTask" class="add-button">追加</button>
    </div>

    <div class="filter-section">
      <button
        @click="filter = 'all'"
        :class="{ active: filter === 'all' }"
        class="filter-button"
      >
        すべて ({{ tasks.length }})
      </button>
      <button
        @click="filter = 'active'"
        :class="{ active: filter === 'active' }"
        class="filter-button"
      >
        未完了 ({{ activeTasks.length }})
      </button>
      <button
        @click="filter = 'completed'"
        :class="{ active: filter === 'completed' }"
        class="filter-button"
      >
        完了 ({{ completedTasks.length }})
      </button>
    </div>

    <ul class="task-list">
      <li v-for="task in filteredTasks" :key="task.id" class="task-item">
        <input
          type="checkbox"
          v-model="task.completed"
          class="checkbox"
        />
        <span :class="{ completed: task.completed }" class="task-text">
          {{ task.text }}
        </span>
        <button @click="deleteTask(task.id)" class="delete-button">削除</button>
      </li>
    </ul>

    <div v-if="filteredTasks.length === 0" class="empty-state">
      {{ emptyMessage }}
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'

interface Task {
  id: number
  text: string
  completed: boolean
}

const newTask = ref('')
const tasks = ref<Task[]>([])
const filter = ref<'all' | 'active' | 'completed'>('all')
let nextId = 1

const addTask = () => {
  if (newTask.value.trim()) {
    tasks.value.push({
      id: nextId++,
      text: newTask.value.trim(),
      completed: false
    })
    newTask.value = ''
  }
}

const deleteTask = (id: number) => {
  tasks.value = tasks.value.filter(task => task.id !== id)
}

const activeTasks = computed(() => {
  return tasks.value.filter(task => !task.completed)
})

const completedTasks = computed(() => {
  return tasks.value.filter(task => task.completed)
})

const filteredTasks = computed(() => {
  if (filter.value === 'active') {
    return activeTasks.value
  } else if (filter.value === 'completed') {
    return completedTasks.value
  }
  return tasks.value
})

const emptyMessage = computed(() => {
  if (filter.value === 'active') {
    return '未完了のタスクがありません'
  } else if (filter.value === 'completed') {
    return '完了したタスクがありません'
  }
  return 'タスクがありません'
})
</script>

<style scoped>
.task-list-page {
  max-width: 700px;
  margin: 50px auto;
  padding: 20px;
  font-family: Arial, sans-serif;
}

h1 {
  text-align: center;
  color: #333;
  margin-bottom: 20px;
}

.navigation {
  text-align: center;
  margin-bottom: 20px;
}

.nav-link {
  color: #4CAF50;
  text-decoration: none;
  font-size: 16px;
  padding: 8px 16px;
  border: 1px solid #4CAF50;
  border-radius: 4px;
  transition: all 0.3s;
}

.nav-link:hover {
  background-color: #4CAF50;
  color: white;
}

.input-section {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

.task-input {
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
  transition: background-color 0.3s;
}

.add-button:hover {
  background-color: #45a049;
}

.filter-section {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
  justify-content: center;
}

.filter-button {
  padding: 8px 16px;
  background-color: #f0f0f0;
  color: #333;
  border: 1px solid #ddd;
  border-radius: 4px;
  cursor: pointer;
  font-size: 14px;
  transition: all 0.3s;
}

.filter-button:hover {
  background-color: #e0e0e0;
}

.filter-button.active {
  background-color: #2196F3;
  color: white;
  border-color: #2196F3;
}

.task-list {
  list-style: none;
  padding: 0;
}

.task-item {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 12px;
  border: 1px solid #ddd;
  border-radius: 4px;
  margin-bottom: 10px;
  background-color: #f9f9f9;
  transition: background-color 0.3s;
}

.task-item:hover {
  background-color: #f0f0f0;
}

.checkbox {
  width: 20px;
  height: 20px;
  cursor: pointer;
}

.task-text {
  flex: 1;
  font-size: 16px;
}

.task-text.completed {
  text-decoration: line-through;
  color: #999;
}

.delete-button {
  padding: 6px 16px;
  background-color: #f44336;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.delete-button:hover {
  background-color: #da190b;
}

.empty-state {
  text-align: center;
  color: #999;
  padding: 30px;
  font-size: 16px;
  background-color: #f9f9f9;
  border-radius: 4px;
  margin-top: 20px;
}
</style>
