<template>
    <div class="footer-chat">
        <i class="icon fa fa-smile-o clickable" style="font-size:25pt;" aria-hidden="true"></i>
        <input v-bind:value="text" @input="text = $event.target.value" type="text" id="msgInput" class="write-message"
            placeholder="Type your message here">
        <i @click="sendMessage" class="icon send fa fa-paper-plane-o clickable" aria-hidden="true"></i>
    </div>
</template>

<script>
export default {
    name: "footer-chat",
    data() {
        return {
            msg: {
                title: '',
                body: '',
                time: '',
            }
        }
    },
    text: '',
    methods: {
        sendMessage() {
            this.msg.id = Math.floor(Math.random() * 10000)
            this.msg.time = Date.now()
            this.msg.title = this.text
            this.$emit('get_msg', this.msg)
            //Реализовать метод отправки сообщения на бэкенд
            // console.log(this.text)
            this.msg = {
                title: '',
                body: '',
                time: '',
            }
            this.text = ''
            document.getElementById('msgInput').value = ''
        }
    },
    // get_message_from_back() {
    //     this.msg.id = Math.floor(Math.random() * 10000)
    //     this.msg.userId = 1
    //     this.msg.title = this.text
    //     console.log("Click")
    //     const eventSource = new EventSource('http://localhost:8000/')
    //     eventSource.onmessage = function (e) {
    //         this.msg.title = e.data.status
    //         console.log(e.data)
    //     }
    //     this.msg = {
    //         title: '',
    //         body: '',
    //         time: '',
    //     }
    //     this.msg.time = Date.now()
    //     this.$emit('get_msg', this.msg)

    // },
}
</script>

<style>
.footer-chat {
    width: calc(65% - 66px);
    height: 11vh;
    display: flex;
    align-items: center;
    position: absolute;
    bottom: 0;
    background-color: transparent;
    border-top: 2px solid #EEE;
}

.chat .footer-chat .icon {
    margin-left: 30px;
    color: #C0C0C0;
    font-size: 14pt;
}

.chat .footer-chat .send {
    color: #fff;
    background-color: #4f6ebd;
    position: absolute;
    right: 50px;
    padding: 12px 12px 12px 12px;
    border-radius: 50px;
    font-size: 14pt;
}

.chat .footer-chat .name {
    margin: 0 0 0 20px;
    text-transform: uppercase;
    font-family: 'Montserrat', sans-serif;
    font-size: 13pt;
    color: #515151;
}

.chat .footer-chat .right {
    position: absolute;
    right: 40px;
}

.write-message {
    border: none !important;
    width: 60%;
    height: 50px;
    margin-left: 20px;
    padding: 10px;
}

.footer-chat *::-webkit-input-placeholder {
    color: #C0C0C0;
    font-size: 13pt;
}

.footer-chat input *:-moz-placeholder {
    color: #C0C0C0;
    font-size: 13pt;
}

.footer-chat input *::-moz-placeholder {
    color: #C0C0C0;
    font-size: 13pt;
    margin-left: 5px;
}

.footer-chat input *:-ms-input-placeholder {
    color: #C0C0C0;
    font-size: 13pt;
}

.clickable {
    cursor: pointer;
}
</style>