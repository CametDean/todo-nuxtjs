<template>
    <div>
        <h1>Notre super todolist</h1>
        <input type="text" v-model="newTodoItem" v-on:keyup.enter="addNewItem">
        <TodoList :items="list"/>
    </div>
</template>

<script>
import TodoList from "@/components/TodoList"

export default {
    components: { TodoList },
    data() {
        return {
            list: [],
            newTodoItem: '',
            nextTodoId: 1,
        }
    },
    methods: {
        addNewItem(){
            const newItem = { id: this.nextTodoId, text: this.newTodoItem, status: "todo" }
            this.list.push(newItem)
            this.nextTodoId  ++
            this.newTodoItem = ''
        }
    }
}
</script>

<style>
    h1{
        font-size: 30px;
        font-family: 'Roboto', sans-serif;
    }
    
    input{
        width: 100%;
        padding-top: 5px;
        padding-bottom: 5px;
        font-size: 20px;
        font-family: 'Roboto', sans-serif;
    }
</style>