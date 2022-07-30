<template>
    <span class="message text-only">
        <div class="response">
            <p class="text"> Hey Megan ! It's been a while 😃</p>
            <p class="response-time time"> 15h04</p>
        </div>
    </span>
</template>

<script>
export default {
    props: {
        messages: {
            type: Array,
            required: true,
        },
    },
    methods: {
    },
}
</script>

<style>
.response-time {
    float: right;
    margin-right: 40px !important;
}

.response {
    float: right;
    margin-right: 0px !important;
    margin-left: auto;
    /* flexbox alignment rule */
}

.response .text {
    background-color: #e3effd !important;
}
</style>