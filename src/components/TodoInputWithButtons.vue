<template>
    <b-form inline>
        <label class="sr-only" for="inline-form-input-name">Todo input</label>
        <b-form-input
          id="inline-form-input-name"
          class="mb-2 mr-sm-2 mb-sm-0"
          :placeholder="placeholder"
          v-on:keyup.enter.prevent="sendAddTodoMessage"
          v-on:keydown.tab="sendAddTodoMessage"
          v-model="userText"
        ></b-form-input>
        <b-button 
          variant="primary"
          v-on:click="sendAddTodoMessage"
        >
          Add Todo
        </b-button>
        <b-button 
          variant="secondary"
          v-on:click="sendClearAllMessage"
          class="ml-2"
        >
          Clear All
        </b-button>
    </b-form>    
</template>

<script>
import { BForm, BFormInput, BButton } from "bootstrap-vue"

export default {
    name: 'TodoInputWithButtons',
    components: {
        BForm,
        BFormInput,
        BButton,
    },
    data() {
      return {
        userText: "",
      }
    },
    props: {
        placeholder: String,
    },
    emits: [
        'add-todo-message',
        'clear-all-message',
    ],
    methods: {
        sendAddTodoMessage() {
            this.$emit('add-todo-message', this.userText);
            this.userText = "";
        },
        sendClearAllMessage() {
            this.$emit('clear-all-message')
        }
    }

}
</script>