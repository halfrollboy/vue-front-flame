<template>
    <div class="code_block" v-for="eventl in eventslist" :key="eventl.id">{{ eventl.body }} </div>
</template>

<script>
    export default {
        props:{
            eventslist:{
                type: Array,  
                required: true,
            }
        }
    }
</script>

<style>
.code_block{
    margin-bottom: 20px;
    /* height: 30px; */
}

</style>