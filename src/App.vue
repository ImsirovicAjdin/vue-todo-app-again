<template>
  <div id="app">
    <HelloWorld msg="Todo all version 2"/>
    <todo-form />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import TodoForm from './components/TodoForm.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    TodoForm,
  }
}
</script>

<style scoped>
#app {
  max-width: 500px;
  margin: 30px auto;
}
</style>
