<template>
    <div>
    <b-form inline>
        <label class="sr-only" for="inline-form-input-name">Name</label>
        <b-form-input
          id="inline-form-input-name"
          class="mb-2 mr-sm-2 mb-sm-0"
          placeholder="Jane Doe"
          v-on:keyup.enter.prevent="addTodo"
          v-on:keydown.tab="addTodo"
          v-model="someVar"
        ></b-form-input>
        <b-button 
          variant="primary"
          v-on:click="addTodo"
        >
          Add Todo
        </b-button>
        <b-button 
          variant="secondary"
          v-on:click="clearAllTodos"
        >
          Clear All
        </b-button>
    </b-form>

    <div class="mt-5">  <!-- (3) -->
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
import { BForm, BFormInput, BButton } from "bootstrap-vue";

  export default {
    name: 'TodoForm',
    components: {
        BForm,
        BFormInput,
        BButton,
    },
    data() {
      return {
        heading: "Todo app in Vue 2.6, pt 7",
        placeholder: "Add your todo here",
        todos: [],
        someVar: "",
      }
    },
    methods: {
      addTodo() {
        console.log(this.someVar);
        this.todos.push({ description: this.someVar, isDone: false });
        this.someVar = "";
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