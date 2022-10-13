<template>
    <InputText type="text" v-model="todoString" />
</template>

<script>
import { ref } from 'vue';

export default {
    setup() {
        const todoString = ref();

        return { todoString }
    }
}
</script>