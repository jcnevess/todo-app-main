<script setup>
const { task } = defineProps(['task'])
const emit = defineEmits(['toggleCompleteTask', 'deleteTask'])
</script>

<template>
  <div class="task content-box" :class="{ 'task-completed': task.completed }" draggable="true">
    <div class="task-main">
      <div class="task-icon" role="button" @click="emit('toggleCompleteTask', task.id)"></div>
      <div class="task-text" @click="emit('toggleCompleteTask', task.id)">{{ task.text }}</div>
    </div>
    <div class="delete-icon" role="button" @click="emit('deleteTask', task.id)">
      <img src="@/assets/images/icon-cross.svg" alt="delete" />
    </div>
  </div>
</template>

<style scoped>
.task {
  border-bottom: 1px solid var(--color-light-grayish-blue);
  display: flex;
  justify-content: space-between;
}

.task-completed > .task-main > .task-icon {
  background-image: url('@/assets/images/icon-check.svg'), var(--gradient-check);
  background-repeat: no-repeat;
  background-position: center;
  background-position-y: 60%;
}

.task-completed > .task-main > .task-text {
  color: var(--color-light-grayish-blue);
  text-decoration: line-through;
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

.task-main {
  display: flex;
  gap: 0.75rem;
  align-items: center;
}

.task-icon {
  width: 20px;
  aspect-ratio: 1;
  border-radius: 50%;
  border: 1px solid var(--color-lightest-grayish-blue);
  cursor: pointer;
}

.task-icon:active,
.task-icon:hover {
  border-color: var(--color-darkest-grayish-blue);
}

.task-text {
  font-size: 0.6rem;
  cursor: pointer;
}

.delete-icon {
  cursor: pointer;
}

.delete-icon img {
  width: 15px;
  aspect-ratio: 1;
  border-radius: 50%;
}

[data-theme='dark'] {
  .task {
    border-color: var(--color-darkest-grayish-blue-2);
  }

  .task-completed > .task-main > .task-text {
    color: var(--color-dark-grayish-blue);
  }

  .content-box {
    background-color: var(--color-dark-dessat-blue);
  }

  .task-icon {
    border-color: var(--color-darkest-grayish-blue-2);
  }

  .task-text {
    color: var(--color-light-grayish-blue);
  }
}
</style>
