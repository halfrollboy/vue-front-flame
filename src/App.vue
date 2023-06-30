<template>
    <div class="app">
        <div class="str">
            <div class="column">
                <card-form
                v-on:sse-event="testMethod"
                :saveCardList="saveCardList"
                :user_id="user_id"
                />
            </div>
            <div class="column codes">
                <event-list :eventslist="eventslist"/>
            </div> 
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import CardForm from "@/components/CardForm.vue";
import EventList from "@/components/EventList.vue";
export default {
    components:{
        CardForm, EventList
    },
    data() {
        return {
            eventslist: [
                {id:1,body:"111['sdfsdfsd']"},
                {id:2,body:"111['sdfsdfsd']"},
                {id:3,body:"111['sdfsdfsd']"},
                {id:1,body:"111['sdfsdfsd']"},
                {id:2,body:"111['sdfsdfsd']"},
                {id:3,body:"111['sdfsdfsd']"},
            ],
            user_id: "",
            saveCardList:[
                {id: "one" ,type: "bank_card",data: {last4: "4567"}},
            ]
        }
    },
    methods:{
        testMethod(data){
            console.log("Принял - ",data);
            this.eventslist.push(data);
        },
        fetchData() {
            //Фетчим карты чтобы они отображались в интерфейсе
            axios.get('http://localhost:8082/method/all/'+ this.user_id)
            .then(response => {
                console.log(response.data);
                this.saveCardList.push(response.data);
            })
            .catch(error => {
                console.error(error);
            });
        }
    },
    mounted() {
        
        var uuidv4 = () => {
            return 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g, function(c) {
                var r = Math.random() * 16 | 0, v = c == 'x' ? r : (r & 0x3 | 0x8);
                return v.toString(16);
            })};

        this.user_id = uuidv4()
        setInterval(() => {
            this.fetchData();
        }, 5000);
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