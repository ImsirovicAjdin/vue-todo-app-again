<template>
    <div>
        <b-form-input v-model="text" placeholder="Enter your name"></b-form-input>
        <div class="mt-2">Value: {{ text }}</div>
    </div>
</template>

<script>
import { BFormInput } from "bootstrap-vue"

export default {
    name: 'TodoINputField',
    components: [
        BFormInput,
    ],
    data() {
        return {
            text: ''
        }
    }
}
</script>
