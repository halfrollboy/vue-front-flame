<template>
    <div class="discussion">
        <div class="photo"
            style="background-image: url(https://i.pinimg.com/originals/a9/26/52/a926525d966c9479c18d3b4f8e64b434.jpg);">
            <div class="online"></div>
        </div>
        <div class="desc-contact">
            <p class="name">{{ name }}</p>
            <p class="message">{{ message }}</p>
        </div>
        <div class="timer">{{ time_msg }}</div>
    </div>
</template>

<script>
export default {
    name: "my-input",
    time_msg: time_msg,
    message: "new_message",
    methods: {}
}
</script>

<style>
.discussion:not(.search):hover {
    background-color: #cfcbf1;
    opacity: 85%;
}

.discussions .discussion {
    width: 100%;
    height: 90px;
    background-color: #FAFAFA;
    border-bottom: solid 1px #E0E0E0;
    display: flex;
    align-items: center;
    cursor: pointer;
}

.discussions .message-active {
    width: 98.5%;
    height: 90px;
    background-color: #FFF;
    border-bottom: solid 1px #E0E0E0;
}

.discussions .discussion .photo {
    margin-left: 20px;
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


.discussions .discussion .name {
    margin: 0 0 0 20px;
    font-family: 'Montserrat', sans-serif;
    font-size: 11pt;
    color: #515151;
}

.discussions .discussion .message {
    margin: 6px 0 0 20px;
    font-family: 'Montserrat', sans-serif;
    font-size: 9pt;
    color: #515151;
}


/* Отображение пользователя в сети*/
.online {
    /* position: relative; */
    top: 30px;
    left: 35px;
    width: 13px;
    height: 13px;
    background-color: #8BC34A;
    border-radius: 13px;
    border: 3px solid #FAFAFA;
}

.timer {
    margin-left: 15%;
    font-family: 'Open Sans', sans-serif;
    font-size: 11px;
    padding: 3px 8px;
    color: rgb(120, 120, 120);
    background-color: #FFF;
    border: 1px solid #E5E5E5;
    border-radius: 15px;
}
</style>