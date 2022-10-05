<template>
    <section class="chat">
        <div class="messages-chat" id="chatBlock">
            <message-item v-for="message in messages" :key="message.id" :message="message" />
            <footer-chat @get_msg="send_msg_to_chat" />
            <button @click="get_message_from_back"></button>
        </div>
    </section>
</template>

<script>
import messageItem from './UI/messageItem.vue'
import footerChat from './UI/footerChat.vue'
export default {
    components: { messageItem, footerChat },
    name: "chat-list",
    data() {
        return {
            messages: [
                {
                    "userId": 1,
                    "id": 1,
                    "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
                    "body": "quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto"
                },
                {
                    "userId": 2,
                    "id": 2,
                    "title": "qui est esse",
                    "body": "est rerum tempore vitae\nsequi sint nihil reprehenderit dolor beatae ea dolores neque\nfugiat blanditiis voluptate porro vel nihil molestiae ut reiciendis\nqui aperiam non debitis possimus qui neque nisi nulla"
                },
                {
                    "userId": 2,
                    "id": 3,
                    "title": "ea molestias quasi exercitationem repellat qui ipsa sit aut",
                    "body": "et iusto sed quo iure\nvoluptatem occaecati omnis eligendi aut ad\nvoluptatem doloribus vel accusantium quis pariatur\nmolestiae porro eius odio et labore et velit aut"
                },
                {
                    "userId": 1,
                    "id": 4,
                    "title": "eum et est occaecati",
                    "body": "ullam et saepe reiciendis voluptatem adipisci\nsit amet autem assumenda provident rerum culpa\nquis hic commodi nesciunt rem tenetur doloremque ipsam iure\nquis sunt voluptatem rerum illo velit"
                },
                {
                    "userId": 2,
                    "id": 5,
                    "title": "nesciunt quas odio",
                    "body": "repudiandae veniam quaerat sunt sed\nalias aut fugiat sit autem sed est\nvoluptatem omnis possimus esse voluptatibus quis\nest aut tenetur dolor neque"
                },
                {
                    "userId": 2,
                    "id": 6,
                    "title": "dolorem eum magni eos aperiam quia",
                    "body": "ut aspernatur corporis harum nihil quis provident sequi\nmollitia nobis aliquid molestiae\nperspiciatis et ea nemo ab reprehenderit accusantium quas\nvoluptate dolores velit et doloremque molestiae"
                },]
        }
    },
    methods: {
        get_message_from_back() {
            var newMessage = {
                userId: 1,
                body: "какой-то текст"
            }
            const eventSource = new EventSource('http://localhost:8080/sse/4ea558c3-dbbc-44f4-8a51-c58dbe962275')
            eventSource.onmessage = (e) => {
                console.log(e)
                newMessage.title = e.data
                // console.log(this.messages[0].body);
                console.log(newMessage)
                this.send_msg_to_chat(newMessage)
            }

        },
        send_msg_to_chat(msg) {
            //Сюда отправлять сообщение от себя через f
            this.messages.push(msg)
        }
    },
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
