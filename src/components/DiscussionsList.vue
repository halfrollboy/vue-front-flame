<template>
    <section class="discussions">
        <search-input />
    </section>
</template>

<script>
import searchInput from './UI/searchInput.vue'
// import discussionDialog from './UI/discussionDialog.vue';

export default {
    comments: {
        searchInput,
    },
    props: {
        discussions: {
            type: Array,
            required: true,
        },
    },
    methods: {

    },
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

.desc-contact {
    height: 43px;
    width: 50%;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}
</style>