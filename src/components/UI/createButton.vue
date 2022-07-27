<template>
    <button class="btn">
        <slot></slot>
    </button>
</template>
<script>
export default {
    name: "create-button"
}
</script>
<style>
.btn {
    color: black;
    align-self: flex-end;
    background-color: rgb(3, 158, 158);
    padding: 10px 15px;
    border: 2px solid teal;
}
</style>