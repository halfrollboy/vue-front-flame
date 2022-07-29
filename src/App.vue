<template>
    <div class="app">
        <div class="container">
            <div class="row">
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return
    }
}
</script>

<style>
body {
    padding: 0%;
    background-color: #2b303f;
}

.container {
    padding: 0;
    background-color: #FFF;
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.19), 0 6px 6px rgba(0, 0, 0, 0.23);
    height: 100vh;
}

/*Убрать полосу прокрутки для всей страницы*/
::-webkit-scrollbar {
    width: 0;
}
</style>