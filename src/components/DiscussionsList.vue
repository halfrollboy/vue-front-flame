<template>
    <section class="discussions">
        <search-input />
        <discussion-dialog v-for="discussion in discussions" :key="discussion.id" :discussion="discussion" />
    </section>
</template>

<script>
import searchInput from './UI/searchInput.vue'
import discussionDialog from './UI/discussionDialog.vue';
export default {
    name: "discussions-list",
    comments: {
        discussionDialog,
        searchInput,
    },
    data() {
        return {
            discussions: [
                {
                    id: 1,
                    name: "Yurij",
                    message: "Привет я тут",
                    time: "15h",
                },
                {
                    id: 2,
                    name: "Bogan",
                    message: "Я здесь",
                    time: "15h",
                },
                {
                    id: 3,
                    name: "Ksenia",
                    message: "Я забыла носки",
                    time: "15h",
                },
                {
                    id: 4,
                    name: "Саня",
                    message: "Хэлло го кодить",
                    time: "15h",
                },
                {
                    id: 4,
                    name: "Саня",
                    message: "Хэлло го кодить",
                    time: "15h",
                },
                {
                    id: 4,
                    name: "Саня",
                    message: "Хэлло го кодить",
                    time: "15h",
                },
                {
                    id: 4,
                    name: "Саня",
                    message: "Хэлло го кодить",
                    time: "15h",
                },
                {
                    id: 4,
                    name: "Саня",
                    message: "Хэлло го кодить",
                    time: "15h",
                },
                {
                    id: 4,
                    name: "Саня",
                    message: "Хэлло го кодить",
                    time: "15h",
                },
                {
                    id: 4,
                    name: "Саня",
                    message: "Хэлло го кодить",
                    time: "15h",
                },
                {
                    id: 4,
                    name: "Саня",
                    message: "Хэлло го кодить",
                    time: "15h",
                },
                {
                    id: 4,
                    name: "Саня",
                    message: "Хэлло го кодить",
                    time: "15h",
                },
                {
                    id: 4,
                    name: "Саня",
                    message: "Хэлло го кодить",
                    time: "15h",
                },
                {
                    id: 4,
                    name: "Саня",
                    message: "Хэлло го кодить",
                    time: "15h",
                },
                {
                    id: 5,
                    name: "Некит",
                    message: "я дышу пупком это правда очень сложно и непонятно что вообще делать с этим",
                    time: "15h",
                },
            ],
        }
    }
}
</script>

<style>
.discussions {
    width: 35%;
    height: 100vh;
    box-shadow: 0px 8px 10px rgba(0, 0, 0, 0.20);
    overflow-y: auto;
    background-color: #87a3ec;
    display: inline-block;
}
</style>