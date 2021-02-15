<template>
    <div>
    <todo-input-with-buttons
        :placeholder="placeholder"
        v-on:add-todo-message="addTodo"
        v-on:clear-all-message="clearAllTodos"
    />

    <div class="mt-5">
        <ul class="lead">
        <li v-for="(todo, index) in todos" class="py-1" v-bind:key="index">
            <button
              v-if="!todo.isDone"
              class="btn btn-sm btn-success mr-2"
              v-on:click="todo.isDone = !todo.isDone"
            >
            to do
            </button>
            <button
              v-else
              class="btn btn-sm btn-secondary mr-2"
              v-on:click="todo.isDone = !todo.isDone"
            >
            done
            </button>

            <button
              class="btn btn-sm btn-danger mr-2"
              v-on:click="deleteSingleTodo(index)"
            >
              x
            </button>
            <span
              v-bind:class="{strikethrough:todo.isDone}"
            >
              {{ todo.description }}
            </span>
        </li>
        </ul>
    </div>

    </div>
</template>

<script>
import TodoInputWithButtons from "./TodoInputWithButtons.vue"

  export default {
    name: 'TodoForm',
    components: {
        TodoInputWithButtons,
    },
    data() {
      return {
        heading: "Todo app in Vue 2.6, pt 7",
        placeholder: "Add your todo here",
        todos: [],
      }
    },
    methods: {
      addTodo(receiveduserText) {
        console.log(receiveduserText);
        this.todos.push({ description: receiveduserText, isDone: false });
      },
      deleteSingleTodo(index) {
        console.log(this.todos[index]);
        this.todos.splice(index, 1);
      },
      clearAllTodos() {
          if (confirm("Are you sure?")) {
            this.todos = [];
          }
      },
    },
  }
</script>

<style scoped>
ul {
  padding: 0;
}

li {
  list-style-type: none;
}
.strikethrough {
  text-decoration: line-through;
  opacity: 0.25
}
</style>