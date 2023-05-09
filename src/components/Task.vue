<script>

export default {
    name: "Task",

    props: {
        task: Object
    },

    methods: {
        onDelete(id) {
            this.$emit("task-delete", id)
        }
    }

}
</script>

<template>
    <div @click="onDelete(task.id)" class="task">
        <div class="text">
            <img class="delete" src="https://www.svgrepo.com/show/486886/trashcan.svg">
            <h3>{{task.text}}</h3>
            <p>{{task.day}}</p>
        </div>
        <div :class="task.completed ? 'tick' : 'invis'">
            <img src="https://img.uxwing.com/wp-content/themes/uxwing/download/checkmark-cross/tick-green-icon.svg">
        </div>
    </div>
</template>

<style>
    .task {
        position: relative;
        background-color: #060047;
        margin: 10px;
        padding: 10px;
        border-radius: 10px;
        cursor: pointer;
        justify-items: center;
        display: flex;
        flex-direction: row;
        align-items: center;
        filter: drop-shadow(3px 5px 2px rgb(0 0 0 / 0.4));
        max-height: 70px;
        transition: 0.5s;
    }

    .invis {
      opacity: 0;
    }

    .delete {
      position: absolute;
      max-height: 60px;
      left: 50%;
      top: 50%;
      transform: translate(-50%, -50%);
      opacity: 0;
      transition: opacity 0.5s;
    }

    .task:hover .delete {
      opacity: 1;
      transition: opacity 0.5s;
    }

    .task:hover .tick {
      filter: blur(3px) drop-shadow(3px 5px 2px rgb(0 0 0 / 0.4));
      -webkit-filter: blur(3px) drop-shadow(3px 5px 2px rgb(0 0 0 / 0.4));
      transition: 0.5s;
    }

    .task:hover {
      background-color: red;
      transition: 0.5s;
      color: transparent;
      text-shadow: 0 0 8px #000;
    }

    .task:hover .text {
        text-shadow: 0 0 8px #000;
    }

    .text {
      flex: 1;
        color: black;
    }

    .tick {
        width: 10%;
        height: auto;
        display: flex;
        justify-content: center;
        filter: drop-shadow(3px 5px 2px rgb(0 0 0 / 0.4));
        transition: filter 0.5s;
    }




</style>