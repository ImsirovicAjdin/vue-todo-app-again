<template>
  <div id="app">
    <HelloWorld msg="Todo all version 2"/>
    <todo-input-field />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import TodoInputField from './components/TodoInputField.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    TodoInputField,
  }
}
</script>
