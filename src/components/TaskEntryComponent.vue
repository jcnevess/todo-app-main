<script setup>
import { ref } from 'vue'

const emit = defineEmits(['addTask'])

const newTaskText = ref('')

function handleSubmit() {
  emit('addTask', newTaskText.value)
  newTaskText.value = ''
}
</script>

<template>
  <form class="entry-box content-box" @submit.prevent="handleSubmit">
    <label for="enter-task">
      <div class="task-icon" aria-label="Add Task"></div>
    </label>
    <input
      id="enter-task"
      class="task-enter"
      type="text"
      placeholder="Create a new todo..."
      autocomplete="false"
      v-model="newTaskText"
      required="true"
    />
  </form>
</template>

<style scoped>
.entry-box {
  border-radius: 5px;
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

.task-icon {
  width: 20px;
  aspect-ratio: 1;
  border-radius: 50%;
  border: 1px solid var(--color-lightest-grayish-blue);
  cursor: pointer;
}

.task-enter {
  font-family: 'Josefin Sans', sans-serif;
  font-size: 0.65rem;
  border: none;
  height: 24px;
  width: 100%;
  caret-color: var(--color-bright-blue);
}

.task-enter:focus-visible {
  outline: none;
}

.task-enter::placeholder {
  font-weight: 700;
  color: var(--color-dark-grayish-blue);
  font-size: 0.6rem;
  font-family: 'Josefin Sans', sans-serif;
}

[data-theme='dark'] {
  .content-box {
    background-color: var(--color-dark-dessat-blue);
  }

  .task-icon {
    border-color: var(--color-darkest-grayish-blue-2);
  }

  .task-enter {
    color: var(--color-light-grayish-blue);
    background-color: var(--color-dark-dessat-blue);
  }
}
</style>
