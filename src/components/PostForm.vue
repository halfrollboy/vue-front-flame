<template>
    <form @submit.prevent>
        <strong>Созадть пост</strong>
        <my-input v-model:value="post.title" type="text" placeholder="title" />
        <my-input v-model="post.body" type="text" placeholder="body" />
        <create-button class="btn" @click="createPost" style="margin-top: 10px;">Создать
        </create-button>
    </form>
</template>

<script>
export default {
    data() {
        return {
            post: {
                title: "",
                body: "",
            }
        };
    },
    methods: {
        createPost() {
            this.post.id = Date.now();
            this.$emit("create", this.post);
            this.post = {
                title: "",
                body: ""
            };
        }
    },
}
</script>

<style>
form {
    display: flex;
    flex-direction: column;
}

.app {
    padding: 20px;
}
</style>