<template>
    <div class="chat-list">New chat yepps {{ name }}</div>
</template>

<script>
export default {
    data() {
        return {
            name: "Yura"
        };
    }
}
</script>

<style>
.chat-list {
    padding: 20px;
    background-color: rgb(204, 200, 248);
    width: 100px;
    overflow: auto;
    max-height: 100vh;
}
</style>