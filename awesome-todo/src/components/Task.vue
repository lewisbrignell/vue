<template>
  <li>
    <div>{{ index + 1 }}: <slot></slot></div>
    <small>{{ task.dueDate }} @ {{ task.dueTime }}</small>
    <button @click="deleteTask(tasks, index)">x</button>
  </li>
</template>

<script>
export default {
  props: ['task', 'index', 'tasks'],
  methods: {
    deleteTask (tasks, index) {
      tasks.splice(index, 1)
    }
  }
}
</script>

<style>

</style>
