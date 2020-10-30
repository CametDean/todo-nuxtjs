<template>
    <div>
        <li>{{ text }}</li>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: [ "text" ],
}
</script>