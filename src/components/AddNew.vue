<template>
    <h5>Enter your todo</h5>
    <InputText type="text" v-model="todoString" />
    <button @click="$emit('on-add', todoString)">
        Add
    </button>
    <button @click="$emit('on-toggle')">
        Close
    </button>
</template>

<style>

</style>

<script>
import InputText from 'primevue/inputtext'
export default {
    name: 'AddNew',
    // setup() {
    //     const value = ref();
    //     return { value }
    // },
    data() {
        let todoString = "";
        return {
            todoString
        }
    },
    components: {
        InputText
    },
    methods: {
        
    }
}
</script>