<template>
    <div v-for="(item ) in todoList" :key="item.id">
        <div class="todo_text">{{item.todoString}}</div>
        <button @click="$emit('on-delete', item.id)">
            Delete 
        </button>
        <!-- <button  v-if="!edit" @click="toggleEdit(item.todoString)">
            Edit 
        </button>
        <button v-else @click="updateTodo(item.id)">
            Update
        </button> -->
        <input type="text" v-if="edit" v-model="todoString"/>
        <button v-if="!item.completed" @click="$emit('on-complete', item.id)">
            Mark Complete 
        </button>
        <button v-else @click="$emit('on-complete', item.id)">
            Mark In-Complete 
        </button>
    </div>
</template>

<script>

export default {
    name: "TodoList",
    props: {
        todoList: Array
    },
    data() {
        let edit = false;
        let todoString = '';
        return { edit, todoString }
    },
    methods: {
        toggleEdit(arg) {
            this.edit = !this.edit;
            if(this.edit === true)
            this.todoString = arg
        },
        updateTodo(itemId) {
            this.toggleEdit();
            this.$emit('on-update', itemId, this.todoString)
        }
    }
}
</script>