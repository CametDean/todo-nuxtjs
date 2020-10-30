<template>
    <div>
        <ul>
            <TodoItem v-for="singleItem in items" :key="singleItem.id" :text="singleItem.text"/>
        </ul>
    </div>
</template>

<script>
import TodoItem from "@/components/TodoItem"

export default {
    name: "TodoList",
    props: ["items"],
    components: { TodoItem }
}
</script>