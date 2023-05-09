<template>
    <div class="container">
        <CHeader @toggle-add-tasks="toggleShowAddTask" title="ToDo List" :showAddTasks="showAddTasks"></CHeader>

        <div v-if="showAddTasks">
            <AddTask @task-create="createTask"></AddTask>
        </div>

        <Tasks @task-delete="deleteTask" :tasks="tasks"></Tasks>
    </div>
</template>

<script>
  import CHeader from "./components/CHeader.vue";
  import Tasks from "./components/Tasks.vue";
  import AddTask from "./components/AddTask.vue";

  export default {
      name: "App",
      components: {
          CHeader,
          Tasks,
          AddTask
      },

      methods: {
          deleteTask(id) {
              if (confirm("Do you want to delete this task?")) {
                  this.tasks = this.tasks.filter(task => task.id !== id)
              }
          },

          createTask(task) {
              this.tasks = [...this.tasks, task]
          },

          toggleShowAddTask() {
            this.showAddTasks = !this.showAddTasks
          }
      },

      data() {
          return {
              tasks: [],
              showAddTasks: false
          }
      },

      created() {
        return this.tasks = [
            {
                id: 0,
                text: "Single Task 0",
                day: "March 1st at 2:40pm",
                completed: true
            }
        ]
      }
  }

</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

  * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      color: white;
  }

  body {
      background-color: #01000e;
      font-family: 'Poppins', sans-serif;
  }

  .container {
      max-width: 500px;
      margin: 30px auto;
      overflow: auto;
      min-height: 300px;
      padding: 30px;
      border-radius: 5px;
      background-color: #04002b;
      box-shadow: 0px 0px 20px 3px #B3005E;
  }

  .btn {
      display: inline-block;
      background: #000;
      color: #fff;
      border: none;
      padding: 10px 20px;
      margin: 5px;
      border-radius: 5px;
      cursor: pointer;
      text-decoration: none;
      font-size: 15px;
      font-family: inherit;
  }

  .btn:focus {
      outline: none;
  }

  .btn:active {
      transform: scale(0.98);
  }

  .btn-block {
      display: block;
      width: 100%;
  }
</style>