<template>
  <div class="todo-container">
    <h1>Ma Liste de Tâches</h1>
    
    <!-- Formulaire d'ajout de tâche -->
    <div class="add-todo">
      <input 
        v-model="newTodo" 
        @keyup.enter="addTodo"
        placeholder="Ajouter une nouvelle tâche"
        type="text"
      >
      <button @click="addTodo" :disabled="!newTodo.trim()">
        Ajouter
      </button>
    </div>

    <!-- Liste des tâches -->
    <TransitionGroup name="todo-list" tag="ul" class="todo-list">
      <li v-for="todo in todos" :key="todo.id" :class="{ completed: todo.completed }">
        <div class="todo-item">
          <input 
            type="checkbox" 
            :checked="todo.completed"
            @change="toggleTodo(todo.id)"
            class="todo-checkbox"
          >
          <span class="todo-text">{{ todo.text }}</span>
          <button @click="deleteTodo(todo.id)" class="delete-btn">
            Supprimer
          </button>
        </div>
      </li>
    </TransitionGroup>

    <!-- Statistiques -->
    <div class="todo-stats" v-if="todos.length > 0">
      <p>{{ completedCount }} terminée(s) sur {{ todos.length }} tâche(s)</p>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import { TransitionGroup } from 'vue'

const todos = ref([])
const newTodo = ref('')

// Ajouter une nouvelle tâche
const addTodo = () => {
  if (newTodo.value.trim()) {
    todos.value.push({
      id: Date.now(),
      text: newTodo.value,
      completed: false
    })
    newTodo.value = ''
  }
}

// Supprimer une tâche
const deleteTodo = (id) => {
  todos.value = todos.value.filter(todo => todo.id !== id)
}

// Basculer l'état d'une tâche
const toggleTodo = (id) => {
  const todo = todos.value.find(todo => todo.id === id)
  if (todo) {
    todo.completed = !todo.completed
  }
}

// Calculer le nombre de tâches terminées
const completedCount = computed(() => {
  return todos.value.filter(todo => todo.completed).length
})
</script>

<style scoped>
.todo-container {
  max-width: 600px;
  margin: 0 auto;
  padding: 2rem;
}

h1 {
  color: #2c3e50;
  text-align: center;
  margin-bottom: 2rem;
}

.add-todo {
  display: flex;
  gap: 1rem;
  margin-bottom: 2rem;
}

input[type="text"] {
  flex: 1;
  padding: 0.5rem;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-size: 1rem;
}

button {
  padding: 0.5rem 1rem;
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 1rem;
}

button:disabled {
  background-color: #a8d5c2;
  cursor: not-allowed;
}

.todo-list {
  position: relative;
  list-style: none;
  padding: 0;
  min-height: 50px;
}

.todo-item {
  display: flex;
  align-items: center;
  padding: 1rem;
  background-color: #f8f9fa;
  margin-bottom: 0.5rem;
  border-radius: 4px;
  gap: 1rem;
  transition: background-color 0.3s ease;
}

.todo-text {
  flex: 1;
  transition: all 0.4s ease;
  position: relative;
}

.completed .todo-text {
  text-decoration: line-through;
  color: #6c757d;
  opacity: 0.7;
  transform: scale(0.98);
}

.todo-checkbox {
  appearance: none;
  -webkit-appearance: none;
  width: 20px;
  height: 20px;
  border: 2px solid #42b983;
  border-radius: 4px;
  outline: none;
  cursor: pointer;
  position: relative;
  transition: all 0.3s ease;
}

.todo-checkbox:checked {
  background-color: #42b983;
  border-color: #42b983;
  animation: checkbox-pop 0.3s ease-out;
}

.todo-checkbox:checked::after {
  content: '✓';
  position: absolute;
  color: white;
  font-size: 14px;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}

@keyframes checkbox-pop {
  0% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.2);
  }
  100% {
    transform: scale(1);
  }
}

.delete-btn {
  background-color: #dc3545;
}

.delete-btn:hover {
  background-color: #c82333;
}

.todo-stats {
  margin-top: 2rem;
  text-align: center;
  color: #6c757d;
}

/* Animations pour l'ajout et la suppression */
.todo-list-enter-active {
  transition: all 0.5s ease;
}

.todo-list-leave-active {
  transition: all 0.8s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}

.todo-list-enter-from {
  opacity: 0;
  transform: translateX(-30px);
}

.todo-list-leave-to {
  opacity: 0;
  transform: translateX(100px) scale(0.8);
}

/* Animation pour le réarrangement des éléments */
.todo-list-move {
  transition: transform 0.8s ease;
}

/* Assurer que l'élément supprimé n'interfère pas avec l'animation */
.todo-list-leave-active {
  position: absolute;
  width: 100%;
  pointer-events: none;
}

.todo-item.todo-list-leave-active {
  background-color: #ffe5e5;
}
</style>
