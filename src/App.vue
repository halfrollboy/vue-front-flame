<template>
    <div class="app">
        <div class="str">
            <div class="column">
                <card-form/>
            </div>
            <div class="column codes">
                <event-list :events="events"/>
            </div> 
        </div>
    </div>
</template>

<script>
import CardForm from "@/components/CardForm.vue";
import EventList from "@/components/EventList.vue";
export default {
    components:{
        CardForm, EventList
    },
    data() {
        return {
            events: [
                {'body':"111['sdfsdfsd']"},
                {'body':"122['sdfsdfsd']"},
                {'body':"133['sdfsdfsd']"},
            ],
        }
    }
}
</script>

<style>
*{
    margin:0;
    padding:0;
    box-sizing: border-box;
    height: 100%;
    width: 100%;
}

.str{
    display: flex;
    justify-content:center;
    align-items: center;
}
.column {
    display: flex;
    align-items: center;
    align-self: center;
    justify-content: center;
}

.app{
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.codes{
    flex-direction: column-reverse;
    justify-content: flex-start;
    align-items: start;
    align-self: flex-start;
    background-color: rgb(240, 234, 234);
    color:brown;
    padding: 50px;
    overflow: auto; 
}

</style>