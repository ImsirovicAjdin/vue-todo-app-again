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
    </div>
</template>

<script>
import { BForm, BFormInput, BButton } from "bootstrap-vue"

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
        clearAllTodos() {
            if (confirm("Are you sure?")) {
                this.todos = [];
            }
        }
    }
}
</script>
