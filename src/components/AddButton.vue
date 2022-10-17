<template>
    <div v-if="isAddNewTodoVisible">
        <AddNew 
            @on-toggle="toggleAddNew()" 
            @on-add="addTodo"
        />
    </div>
    <button v-else @click="toggleAddNew">
        Add New
    </button>
</template>

<script>
import AddNew from './AddNew.vue';
export default {
    data() {
        let isAddNewTodoVisible = false;
        return { isAddNewTodoVisible }
    },
    components: {
        AddNew
    },
    methods: {
        toggleAddNew() {
            this.isAddNewTodoVisible = !this.isAddNewTodoVisible;
        },
        addTodo(str) {
            this.$emit('on-add', str);
            this.toggleAddNew();
        }
    }
}
</script>