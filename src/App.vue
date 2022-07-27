<template>
    <div class="app">
        <h1 style="margin-bottom: 15px">Тестовый мессенжер Аватара</h1>
        <create-button style="margin-bottom: 15px" @click="showDialog">Создать чат</create-button>
        <my-modal v-model:show="dialogVisible">
            <post-form @create="createPost" />
        </my-modal>
        <div class="horizontal-view">
            <chat-list></chat-list>
            <post-list :posts="posts" @remove="removePost" />
        </div>
    </div>
</template>

<script>
import PostForm from "@/components/PostForm"
import PostList from "@/components/PostList"
import ChatList from "./components/ChatList.vue"
import MyModal from "./components/UI/myModal.vue"
import CreateButton from "./components/UI/createButton.vue"
export default {
    components: {
        PostForm,
        PostList,
        MyModal,
        CreateButton,
        ChatList,
        // CreateButton
    },
    data() {
        return {
            posts: [
                { id: 1, title: "JS the best", body: "this first body" },
                { id: 2, title: "Second post", body: "this first body" },
                { id: 3, title: "Third post", body: "this first body" },
            ],
            dialogVisible: false,
        }
    },
    methods: {
        createPost(post) {
            this.posts.push(post);
        },
        removePost(post) {
            this.posts = this.posts.filter(p => p.id !== post.id)
        },
        showDialog() {
            this.dialogVisible = true
        }
    }
}
</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
</style>