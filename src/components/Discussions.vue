<template>
    <section class="discussions">
    </section>
</template>

<script>
import discussionDialog from './UI/discussionDialog.vue';
export default {
    props: {
        discussions: {
            type: Array,
            required: true,
        },
    },
    components: { discussionDialog },
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