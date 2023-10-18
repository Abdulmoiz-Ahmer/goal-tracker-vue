<script setup>
const props = defineProps({
  id: Number,
  description: String,
  completed: Boolean
})
</script>

<template>
  <section class="container-list-item" :key="id">
    <div class="container-list-item-description" :class="{ cut: props.completed }">
      {{ props.description }}
    </div>
    <div class="container-list-item-actions">
      <input
        type="checkbox"
        class="container-list-item-check"
        @click="(event) => $emit('updateItem', props.id, event.target.checked)"
      />
      <button
        type="button"
        class="container-list-item-button"
        @click="$emit('removeItem', props.id)"
      >
        <span class="material-symbols-outlined">remove</span>
      </button>
    </div>
  </section>
</template>

<style scoped>
.container-list-item {
  display: flex;
  justify-content: space-between;
  width: 70%;
  border: 2px solid rgb(53, 59, 73);
  background-color: #ffffff;
  margin-bottom: 10px;
  border-radius: 10px;
  gap: 20px;
  font-size: 20px;
  padding: 20px;
}

.container-list-item-button {
  border-radius: 30%;
  background: #e72b2b;
  display: flex;
  justify-content: center;
  align-items: center;
  border: none;
  float: right;
  cursor: pointer;
  width: 35px;
  padding: 5px;
}

.container-list-item-actions {
  display: flex;
  gap: 20px;
  align-self: center;
}

.container-list-item-check {
  width: 35px;
  height: 35px;
  cursor: pointer;
}

.container-list-item-check:focus,
.container-list-item-check:checked {
  width: 30px;
  accent-color: #2f3640;
}

.cut {
  text-decoration: line-through;
}
</style>
