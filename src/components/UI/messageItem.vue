<template>
    <div>
        <div class="responce-msg">
            <div class="message">
                <div class="photo"
                    style="background-image: url(https://images.unsplash.com/photo-1438761681033-6461ffad8d80?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1050&q=80);">
                    <div class="online"></div>
                </div>
                <p class="text"> 9 pm at the bar if possible 😳</p>
            </div>
            <p class="time"> 15h09</p>
        </div>
        <span class="message text-only">
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
</style>