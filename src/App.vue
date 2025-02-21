<script setup>
import TaskEntryComponent from './components/TaskEntryComponent.vue'
import TaskListComponent from './components/TaskListComponent.vue'
</script>

<template>
  <div class="outer-container">
    <div class="container-image"></div>
    <main class="inner-container">
      <div class="container-header">
        <h1 class="title">todo</h1>
        <div class="mode-icon"></div>
      </div>
      <div class="container-main">
        <TaskEntryComponent></TaskEntryComponent>
        <TaskListComponent></TaskListComponent>
        <div class="list-controls content-box">
          <div class="controls-container">
            <div class="list-control selected-option">all</div>
            <div class="list-control">active</div>
            <div class="list-control">completed</div>
          </div>
        </div>
      </div>
      <div class="container-footer">Drag and drop to reorder list</div>
    </main>
  </div>
</template>

<style scoped>
.outer-container {
  background-color: var(--color-lightest-grayish-blue);
  color: var(--color-darkest-grayish-blue);
  position: relative;
  padding: 2.5rem 1.5rem;
  min-height: 100dvh;
}

.inner-container {
  display: flex;
  flex-direction: column;
  gap: 2rem;
  z-index: 1;
  position: relative;
  max-width: 465px;
  margin: auto;
}

.container-main {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.container-footer {
  text-align: center;
  font-size: 0.7rem;
  font-weight: 700;
  color: var(--color-dark-grayish-blue);
}

.title {
  color: var(--color-light-gray);
  text-transform: uppercase;
  letter-spacing: 0.75ex;
  font-size: 1.5rem;
  font-weight: 600;
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

.container-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  background-image: url('@/assets/images/bg-mobile-light.jpg');
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  height: 35dvh;
}

.container-header {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
}

.mode-icon {
  width: 20px;
  aspect-ratio: 1;
  background-image: url('@/assets/images/icon-moon.svg');
  background-size: contain;
  cursor: pointer;
}

@media (min-width: 520px) {
  .list-controls {
    position: relative;
    width: fit-content;
    background-color: transparent;
    top: -65px;
    left: 120px;
  }

  .container-image {
    background-image: url('@/assets/images/bg-desktop-light.jpg');
  }
}

@media (prefers-color-scheme: dark) {
  .content-box {
    background-color: var(--color-dark-dessat-blue);
  }

  .container-image {
    background-image: url('@/assets/images/bg-mobile-dark.jpg');
  }

  .mode-icon {
    background-image: url('@/assets/images/icon-sun.svg');
  }

  .outer-container {
    background-color: var(--color-dark-blue);
  }

  .container-footer {
    color: var(--color-darkest-grayish-blue);
  }

  .list-control:active,
  .list-control:hover {
    color: var(--color-light-grayish-blue-hover);
  }

  .list-control.selected-option {
    color: var(--color-bright-blue);
  }
}

@media (prefers-color-scheme: dark) and (min-width: 520px) {
  .container-image {
    background-image: url('@/assets/images/bg-desktop-dark.jpg');
  }

  .list-controls {
    background-color: transparent;
  }
}
</style>
