<template>
    <div v-if="isEditing">
        <li><input v-model="text" type="text" v-on:keyup.enter="updateItem"></li>
    </div>
    <div v-else>
        <li v-on:dblclick="itemIsBeingEdited">{{ text }}</li>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: [ "text" ],
    data(){
        return {
            isEditing: false,
        }
    },
    methods: {
        itemIsBeingEdited(){
            return this.isEditing = true
        },
        updateItem(){
            return this.isEditing = false
        },
    },
}
</script>