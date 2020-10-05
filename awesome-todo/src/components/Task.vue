<template>
    <li>
        <div>{{ index + 1 }}: <slot></slot></div>
        <small>{{ task.dueDate }} @ {{ task.dueTime }}</small>
    </li>
</template>

<script>
export default {
  props: ['task', 'index']
}
</script>

<style>

</style>
