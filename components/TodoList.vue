<template>
    <div>
        <ul>
            <TodoItem v-for="singleItem in items" :key="singleItem.id" :text="singleItem.text" :id="singleItem.id" :status="singleItem.status" v-on:delete-todoitem="deleteItem" />
        </ul>
    </div>
</template>

<script>
import TodoItem from "@/components/TodoItem"

export default {
    name: "TodoList",
    props: ["items"],
    components: { TodoItem },
    methods: {
       deleteItem(todoId){
           let indexOfItemToDelete = this.items.findIndex(item => item.id === todoId)
           this.items.splice(indexOfItemToDelete, 1)
       }
    },
}
</script>

<style>
    ul{
        margin: 0;
        margin-top: 1rem;
        padding: 0;
    }
</style>