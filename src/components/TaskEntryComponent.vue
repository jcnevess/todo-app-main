<script setup></script>

<template>
  <div class="entry-box content-box">
    <div class="task-icon"></div>
    <input class="task-enter" type="text" placeholder="Create a new todo..." />
  </div>
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

.task-icon:active,
.task-icon:hover {
  border-color: var(--color-darkest-grayish-blue);
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

@media (prefers-color-scheme: dark) {
  .content-box {
    background-color: var(--color-dark-dessat-blue);
  }

  .task-icon {
    border-color: var(--color-darkest-grayish-blue-2);
  }

  .task-enter {
    background-color: var(--color-dark-dessat-blue);
  }
}
</style>
