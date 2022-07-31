<template>
    <div>
        <div v-if="message.userId === 1" class="responce-msg">
            <div class="message">
                <div class="photo"
                    style="background-image: url(https://images.unsplash.com/photo-1438761681033-6461ffad8d80?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1050&q=80);">
                    <div class="online"></div>
                </div>
                <p class="text"> {{ message.title }}</p>
            </div>
            <p class="time"> 15h09</p>
        </div>
        <span v-else class="message text-only">
            <div class="response">
                <p class="text"> Hey Megan ! It's been a while 😃</p>
                <p class="response-time time"> 15h04</p>
            </div>
        </span>
    </div>
</template>

<script>
export default {
    name: "message-item",
    props: {
        message: {
            type: Object,
            default: () => {

            }
        }
    },
}
</script>

<style>
.chat .messages-chat .message {
    display: flex;
    align-items: center;
    margin-bottom: 8px;
}

.chat .messages-chat .message .photo {
    display: block;
    width: 45px;
    height: 45px;
    background: #E6E7ED;
    -moz-border-radius: 50px;
    -webkit-border-radius: 50px;
    background-position: center;
    background-size: cover;
    background-repeat: no-repeat;
}

.text-only {
    margin-left: 45px;
}

.time {
    font-size: 10px;
    color: lightgrey;
    margin-bottom: 10px;
    margin-left: 85px;
}

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