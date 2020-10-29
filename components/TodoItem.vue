<template>
    <div>
        <li v-for="singleItem in items" :key="singleItem.id">{{ singleItem.text }}</li>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: [ "items" ],
}
</script>