<template>
    <div v-if="isEditing">
        <li><input v-model="currentLabel" type="text" v-on:keyup.enter="updateItem"></li>
    </div>
    <div v-else-if="editedItem === 'edited'">
        <li id="id">
            {{ newLabel }}
            <div class="buttons">
                <button class="edition" v-on:click.prevent="itemIsBeingEdited">Edit</button>
                <button class="suppression" v-on:click.prevent="deleteTodoItem">Delete</button>
            </div>
        </li>
    </div>
    <div v-else>
        <li id="id">
            {{ text }}
            <div class="buttons">
                <button class="edition" v-on:click.prevent="itemIsBeingEdited">Edit</button>
                <button class="suppression" v-on:click.prevent="deleteTodoItem">Delete</button>
            </div>
        </li>
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
        width: 100%;
        list-style: none;
        padding-top: 5px;
        padding-bottom: 5px;
        font-size: 20px;
        font-family: 'Roboto', sans-serif;
        display: flex;
        flex-direction: row;
        justify-content: space-between;
    }

    input{
        padding-top: 5px;
        padding-bottom: 5px;
        font-size: 20px;
        font-family: 'Roboto', sans-serif;
    }

    .edition{
        background: rgb(134, 189, 134);
        border: none;
        padding-top: 5px;
        padding-bottom: 5px;
    }

    .suppression{
        background: rgb(221, 145, 145);
        border: none;
        padding-top: 5px;
        padding-bottom: 5px;
    }

</style>