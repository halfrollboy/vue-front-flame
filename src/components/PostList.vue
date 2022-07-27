<template>
    <div v-if="posts.length > 0">
        <h3>Список постов</h3>
        <post-item :post="post" v-for="post in posts" :key="post.id" @remove="$emit('remove', post)" />
    </div>
    <h2 v-else style="color:gray; opacity: 50%;">Список постов пуст</h2>
</template>

<script>
import PostItem from "./PostItem.vue";
export default {
    props: {
        posts: {
            type: Array,
            required: true,
        }
    },
    components: { PostItem }
}
</script>

<style>
</style>