<template>
    <div class="post">
        <div>
            <div class="post-title"><strong>{{ post.title }}</strong> пост о javascript</div>
            <div class="post-body">{{ post.body }}</div>
        </div>
        <create-button @click="$emit('remove', post)">Удалить</create-button>
    </div>
</template>

<script>
import CreateButton from "./UI/createButton.vue";
export default {
    props: {
        post: {
            type: Object,
            required: true,
        }
    },
    components: { CreateButton }
}
</script>

<style>
.post {
    margin-top: 15px;
    padding: 15px;
    border: 5px solid teal;
    display: flex;
    align-items: center;
    justify-content: space-between;
}
</style>