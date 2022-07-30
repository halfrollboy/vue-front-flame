<template>
    <div class="app">
        <div class="container">
            <div class="row">
                <chat :message="message" />
                <discussions :discussions="discussions" />
            </div>
        </div>
    </div>
</template>

<script>
import Chat from './components/Chat.vue'
import Discussions from './components/Discussions.vue'
export default {
    components: {
        Discussions,
        Chat,
        Discussions
    },
    data() {
        return {
            discussion: [
                { id: 1, title: "JS the best", body: "this first body" },
                { id: 2, title: "Second post", body: "this first body" },
                { id: 3, title: "Third post", body: "this first body" },
            ],
            message: [
                { id: 1, }
            ],
        }
    }
}
</script>

<style>
body {
    padding: 0%;
    background-color: #2b303f;
}

.container {
    padding: 0;
    background-color: #FFF;
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.19), 0 6px 6px rgba(0, 0, 0, 0.23);
    height: 100vh;
}

/*Убрать полосу прокрутки для всей страницы*/
::-webkit-scrollbar {
    width: 0;
}
</style>