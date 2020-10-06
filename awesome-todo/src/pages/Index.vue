<template>
  <q-page padding>
    <ul>
      <task
        v-for="(task, index) in tasks"
        :key="task.id"
        :task="task"
        :index="index"
      >
        {{ task.name }}
        <button @click="deleteTask(index)">x</button>
      </task>
    </ul>
  </q-page>
</template>

<script>
export default {
  data () {
    return {
      tasks: [
        {
          id: 0,
          name: 'groceries',
          dueDate: '2020.10.30',
          dueTime: '8:00'
        },
        {
          id: 1,
          name: 'pay bills',
          dueDate: '2020.10.10',
          dueTime: '11:00'
        },
        {
          id: 2,
          name: 'yoga',
          dueDate: '2020.10.20',
          dueTime: '17:00'
        }
      ]
    }
  },
  methods: {
    deleteTask (index) {
      this.tasks.splice(index, 1)
    }
  },
  components: {
    task: require('components/Task.vue').default
  }
}
</script>

<style>

</style>
