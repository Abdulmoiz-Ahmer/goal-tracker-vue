<script setup>
import AddBar from './components/AddBar.vue'
import ListItem from './components/ListItem.vue'
import { ref } from 'vue'

const list = ref([])

function addListItem(text) {
  list.value.push({
    id: text,
    description: text,
    completed: false
  })
}

function removeListItem(id) {
  const index = list.value.findIndex((element) => element.id === id)
  list.value.splice(index, 1)
}

function updateListItem(id, checked) {
  list.value[id] = { ...list.value[id], completed: checked }
}
</script>

<template>
  <main className="container">
    <header className="header-container">
      <AddBar @add-item="addListItem" />
    </header>
    <main className="container-list">
      <ListItem
        v-for="({ id, description, completed }, index) in list"
        :key="id"
        :id="index"
        :description="description"
        :completed="completed"
        @update-item="updateListItem"
        @remove-item="removeListItem"
      />
    </main>
  </main>
</template>

<style scoped>
.container {
  background-color: #f6f4eb;
  min-height: 100vh;
  height: max-content;
}

.header-container {
  background-color: #6954a4;
  height: 25vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.container-list {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 75vh;
}
</style>
