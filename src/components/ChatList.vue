<template>
    <section class="chat">
        <div class="messages-chat" id="chatBlock">
            <message-item />
        </div>
    </section>
</template>

<script>
import messageItem from './UI/messageItem.vue'
export default {
    comments: { messageItem },
    name: "chat-list",
}
</script>

<style>
.chat {
    width: calc(65% - 85px);
}

.header-chat {
    background-color: #FFF;
    height: 90px;
    box-shadow: 0px 3px 2px rgba(0, 0, 0, 0.100);
    display: flex;
    align-items: center;
}

.chat .header-chat .icon {
    margin-left: 30px;
    color: #515151;
    font-size: 14pt;
}

.chat .header-chat .name {
    margin: 0 0 0 20px;
    text-transform: uppercase;
    font-family: 'Montserrat', sans-serif;
    font-size: 13pt;
    color: #515151;
}

.chat .header-chat .right {
    position: absolute;
    right: 40px;
}

.chat .messages-chat {
    padding: 25px 35px;
}

.messages-chat {
    overflow-y: auto;
    height: calc(100vh - 11vh);
}

.chat .messages-chat .text {
    margin: 0 35px;
    background-color: #f6f6f6;
    padding: 15px;
    border-radius: 12px;
}
</style>
