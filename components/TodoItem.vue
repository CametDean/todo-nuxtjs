<template>
    <div v-if="isEditing">
        <li><input v-model="currentLabel" type="text" v-on:keyup.enter="updateItem"></li>
    </div>
    <div v-else-if="editedItem === 'edited'">
        <li v-on:dblclick="itemIsBeingEdited" id="id">{{ newLabel }} || <button v-on:click.prevent="deleteTodoItem">Delete</button></li>
    </div>
    <div v-else>
        <li v-on:dblclick="itemIsBeingEdited" id="id">{{ text }} || <button v-on:click.prevent="deleteTodoItem">Delete</button></li>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: [ "text", "id", "status" ],
    data(){
        return {
            editedItem: this.status,
            isEditing: false,
            todoId: this.id,
            currentLabel: this.text,
            newLabel: ''
        }
    },
    methods: {
        itemIsBeingEdited(){
            this.isEditing = true
        },
        updateItem(e){
            this.newLabel = this.currentLabel
            this.editedItem = "edited"
            this.isEditing = false
        },
        deleteTodoItem(){
            this.$emit("delete-todoitem", this.todoId)
        }
    },
}
</script>

<style>
    li{
        list-style: none;
        padding-top: 5px;
        padding-bottom: 5px;
        font-size: 20px;
        font-family: 'Roboto', sans-serif;
    }

    input{
        padding-top: 5px;
        padding-bottom: 5px;
        font-size: 20px;
        font-family: 'Roboto', sans-serif;
    }

</style>