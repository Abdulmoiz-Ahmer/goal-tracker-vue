<script setup>
import { ref } from 'vue'
const text = ref('')
const emit = defineEmits(['addItem'])

function onSubmit() {
  emit('addItem', text.value)
  text.value = ''
}
</script>

<template>
  <div class="header-container-searchBar-container">
    <form @submit.prevent="onSubmit()">
      <input
        placeholder="Add Yearly Goals Here..."
        type="text"
        name="searchBar"
        class="header-container-searchBar-container-search"
        v-model="text"
      />

      <button class="header-container-searchBar-container-search-icon" @click="submit">
        <span class="material-symbols-outlined">add</span>
      </button>
    </form>
  </div>
</template>

<style scoped>
.header-container-searchBar-container {
  width: 50%;
  height: 50px;
  border-radius: 50px;
  padding: 10px;
  background-color: rgb(53, 59, 73);
}

.header-container-searchBar-container-search {
  float: left;
  width: 94%;
  height: 100%;
  background-color: transparent;
  border: none;
  color: #ffffff;
  outline-width: 0;
  font-size: 20px;
}

.header-container-searchBar-container-search-icon {
  border-radius: 50%;
  background: #2f3640;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 5px;
  border: none;
  float: right;
  width: 35px;
  cursor: pointer;
}

.material-symbols-outlined {
  font-size: 25px;
  color: #ffffff;
}
</style>
