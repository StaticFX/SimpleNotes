<template>
    <header>
        <h1>{{ title }}</h1>

        <div v-if="!showAddTasks">
            <Button @toggle-add-tasks="$emit('toggle-add-tasks')" text="Add Task" color="#E90064"></Button>
        </div>
        <div v-else>
            <Button @toggle-add-tasks="$emit('toggle-add-tasks')" text="Hide" color="#a30046"></Button>
        </div>

    </header>
</template>

<script>

    import Button from "./Button.vue";

  export default {
      name: "CHeader",
      components: {
          Button
      },
      props: {
          title: String,
          showAddTasks: false
      }
  }

</script>

<style scoped>

    * {
        background-color: #04002b;
    }

    header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
    }

</style>