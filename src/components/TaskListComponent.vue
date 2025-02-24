<script setup>
import { computed, ref } from 'vue'
import TaskComponent from './TaskComponent.vue'

const SHOW_ALL_TASKS = 'all'
const SHOW_ACTIVE_TASKS = 'active'
const SHOW_COMPLETED_TASKS = 'completed'

const { tasks } = defineProps(['tasks'])
const emit = defineEmits(['toggleCompleteTask', 'deleteTask', 'deleteCompleted'])

const visibilityChoice = ref(SHOW_ALL_TASKS)

// IsVisible uses visibilityChoice so it recomputes when the latter changes
const visibleTasks = computed(() => tasks.filter((task) => isVisible(task, visibilityChoice.value)))

function setVisibility(visibility) {
  visibilityChoice.value = visibility
}

function isVisible(task, visibility) {
  if (visibility === SHOW_ACTIVE_TASKS) {
    return !task.completed
  } else if (visibility === SHOW_COMPLETED_TASKS) {
    return task.completed
  } else {
    return true
  }
}
</script>

<template>
  <div class="todo-list">
    <div class="tasks">
      <TaskComponent
        v-for="task in visibleTasks"
        :key="task.id"
        :task
        @delete-task="emit('deleteTask', task.id)"
        @toggle-complete-task="emit('toggleCompleteTask', task.id)"
      ></TaskComponent>
    </div>
    <div class="list-info content-box">
      <div class="items-left">{{ visibleTasks.length }} items left</div>
      <div class="clear-completed" @click="emit('deleteCompleted')">clear completed</div>
    </div>
  </div>
  <div class="list-controls content-box">
    <div class="controls-container">
      <div
        class="list-control"
        :class="{ 'selected-option': visibilityChoice === SHOW_ALL_TASKS }"
        role="button"
        @click="() => setVisibility(SHOW_ALL_TASKS)"
      >
        all
      </div>
      <div
        class="list-control"
        :class="{ 'selected-option': visibilityChoice === SHOW_ACTIVE_TASKS }"
        role="button"
        @click="() => setVisibility(SHOW_ACTIVE_TASKS)"
      >
        active
      </div>
      <div
        class="list-control"
        :class="{ 'selected-option': visibilityChoice === SHOW_COMPLETED_TASKS }"
        role="button"
        @click="() => setVisibility(SHOW_COMPLETED_TASKS)"
      >
        completed
      </div>
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

.list-controls {
  justify-content: center;
  border-radius: 5px;
}

.controls-container {
  display: flex;
  gap: 1rem;
}

.list-control {
  text-transform: capitalize;
  color: var(--color-dark-grayish-blue);
  font-weight: 700;
  cursor: pointer;
}

.list-control:active,
.list-control:hover {
  color: var(--color-darkest-grayish-blue);
}

.list-control.selected-option {
  color: var(--color-bright-blue);
}

[data-theme='dark'] {
  .content-box {
    background-color: var(--color-dark-dessat-blue);
  }

  .clear-completed:active,
  .clear-completed:hover {
    color: var(--color-light-grayish-blue-hover);
  }

  .list-control:active,
  .list-control:hover {
    color: var(--color-light-grayish-blue-hover);
  }

  .list-control.selected-option {
    color: var(--color-bright-blue);
  }
}

@media (min-width: 520px) {
  .list-controls {
    position: relative;
    width: fit-content;
    background-color: transparent;
    top: -65px;
    left: 120px;
  }

  [data-theme='dark'] {
    .list-controls {
      background-color: transparent;
    }
  }
}
</style>
