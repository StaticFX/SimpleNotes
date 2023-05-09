<script>
  export default {
      name: "Button",

      props: {
          text: String,
          color: String
      },

  }
</script>

<template>
  <button @click="$emit('toggle-add-tasks')" class="btn" :style="{backgroundColor: color}">{{text}}</button>
</template>

<style scoped>

</style>