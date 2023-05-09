<template>

  <form @submit="onClick">
      <div>
          <label>Name</label>
          <input type="text" v-model="name" name="name" placeholder="Your Task">
      </div>
      <div>
          <label>Date</label>
          <input type="text" v-model="day" name="date" placeholder="Your Date">
      </div>

      <button>Save Task</button>
  </form>

</template>

<script>

  import Button from "./Button.vue";

  export default {
      name: "AddTask",
      components: {Button},

      methods: {
          onClick(e) {
              e.preventDefault()

              if (!this.name) {
                  alert("Please fill out a name")
                  return
              }
              if (!this.day) {
                  alert("Please fill out a date")
                  return
              }

              const task = {
                  id: Math.floor(Math.random() * 100000),
                  text: this.name,
                  day: this.day,
                  completed: false
              }

              this.name = ""
              this.day = ""

              this.$emit("task-create", task)
          }
      },

      data() {
        return {
            name: '',
            day: ''
        }
      }

  }

</script>

<style scoped>

  button {
      text-align: center;
      width: 100%;
      padding: 10px;
      margin: 5px 3px 3px;
      border: black solid 1px;
      border-radius: 5px;
      background-color: black;
      color: white;
      transition: .3s ease-in-out;
  }

  button:hover {
      background-color: white;
      color: black;
  }

  input {
      background-color: transparent;
      width: 100%;
      border: grey solid 2px;
      border-radius: 5px;
      padding: 5px;
      margin: 3px;
  }


</style>