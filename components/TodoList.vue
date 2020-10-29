<template>
    <div>
        <ul>
            <TodoItem :items="items" />
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