<template>
    <div>
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add Todo....">
            <input type="submit" value="ADD" class="btn">
        </form>
    </div>
</template>

<script>

// import uuid from 'uuid';
// import {uuid} from 'vue-uuid';

export default {
    name: "AddTodo",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();
            const newTodo = {
                title: this.title,
                completed: false
            }
            //Send up to parent
            this.$emit('add-todo', newTodo);
            this.title = '';
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
        margin-top: 1rem;
    }
    input[type="text"] {
        flex: 10;
        padding: 5px;
        outline: none;
        border: 1px solid lightgrey;
    }
    input[type="submit"] {
        flex: 2;
    }
</style>