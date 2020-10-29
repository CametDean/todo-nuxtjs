<template>
    <div>
        <h1>Notre super todolist</h1>
        <input type="text" v-model="newTodoItem">
        <button v-on:click="addNewItem">Add</button>
        <TodoList :items="list"/>
    </div>
</template>

<script>
import TodoList from "@/components/TodoList"

export default {
    components: { TodoList },
    data() {
        return {
            list: [
                {id: 1, text: "croquettes"},
                {id: 2, text: "pain"},
                {id: 3, text: "raisin"},
                {id: 4, text: "fraises"},
                {id: 5, text: "framboises"},
            ],
            newTodoItem: '',
            nextTodoId: 6,
        }
    },
    methods: {
        addNewItem(){
            const newItem = { id: this.nextTodoId, text: this.newTodoItem }
            this.list.push(newItem)
            this.nextTodoId  ++
            this.newTodoItem = ''
        }
    }
}
</script>