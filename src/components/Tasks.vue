<template>
  <div :key="task.id" v-for="task in tasks">
      <Task @task-delete="$emit('task-delete', task.id)" :task="task"></Task>
  </div>
</template>

<script>
  import Task from "./Task.vue";
  export default {
      name: "Tasks",

      components: {
          Task
      },

      props: {
          tasks: []
      },

      emits: [
          "task-delete"
      ]

  }

</script>

<style scoped>

</style>