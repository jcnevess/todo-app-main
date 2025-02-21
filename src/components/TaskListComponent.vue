<script setup>
import TaskComponent from './TaskComponent.vue'
</script>

<template>
  <div class="todo-list">
    <div class="tasks">
      <TaskComponent></TaskComponent>
    </div>
    <div class="list-info content-box">
      <div class="items-left">5 items left</div>
      <div class="clear-completed">clear completed</div>
    </div>
  </div>
</template>

<style scoped>
.todo-list {
  border-radius: 5px;
  overflow: hidden;
}

.list-info {
  color: var(--color-dark-grayish-blue);
  display: flex;
  justify-content: space-between;
  font-size: 0.65rem;
}

.content-box {
  padding: 0.75rem 1rem;
  display: flex;
  align-items: center;
  gap: 0.75rem;
  background-color: white;
  font-size: 0.75rem;
  font-weight: 500;
  height: 48px;
}

.clear-completed {
  text-transform: capitalize;
  cursor: pointer;
}

.clear-completed:active,
.clear-completed:hover {
  color: var(--color-darkest-grayish-blue);
}

@media (prefers-color-scheme: dark) {
  .content-box {
    background-color: var(--color-dark-dessat-blue);
  }

  .clear-completed:active,
  .clear-completed:hover {
    color: var(--color-light-grayish-blue-hover);
  }
}
</style>
