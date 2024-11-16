<script setup>
import TodoList from './components/TodoList.vue'
import { watch } from 'vue'
import { useTitle } from '@vueuse/core'

// Définir le titre de la page
const title = useTitle('Ma Liste de Tâches')
</script>

<template>
  <TodoList />
</template>

<style>
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background-color: #f5f5f5;
}
</style>
