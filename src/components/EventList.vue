<template>
    <div class="code_block" v-for="event in events" v-bind:key="event">{{ event.body }} </div>
</template>

<script>
    export default {
        props:{
            events:{
                type: Array,
                
            }
        }
    }
</script>

<style>
.code_block{
    margin-bottom: 20px;
}

</style>