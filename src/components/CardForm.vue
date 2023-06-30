<template>
<form class="item" @submit.prevent>
    Номер карты<br>
    <input 
        v-model="card.card_number" 
        type="text"
        name="firstname"><br>
    <div class="small_block">
        <input 
            v-model="card.card_holder"  
            class="card_name" 
            type="text"
            name="lastname">
        <input 
            v-model="card.card_data" 
            class="card_date" 
            type="text" 
            name="lastname"></div>
    <div class="small_block">
        <input
            v-model="card.card_cvv"
            class="cvv" 
            type="text" 
            name="lastname" 
            placeholder="CVV" 
            maxlength=3></div>
    <div class="btn"
        @click="get_message_from_back"
        >PAY</div>
</form>
</template>

<script>
import axios from 'axios';
export default {
    emits: ['sse-event'],
    data(){
        return{
            card:{
                id: 0,
                card_number:'5555 5555 5555 4444',
                card_holder:'Taran Yurij',
                card_data:'10/23',
                card_cvv:'666'
            }
        }
    },
    methods:{
        sendForm(e){
            // this.post.id = Date.now()
            // this.card.card_number
            console.log("[eq]",e)
        },
        get_message_from_back() {

            
            var uuidv4 = () => {
            return 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g, function(c) {
                var r = Math.random() * 16 | 0, v = c == 'x' ? r : (r & 0x3 | 0x8);
                return v.toString(16);
            })};
        
            var url = 'http://localhost:8084/sse/sse/' + uuidv4()
            
            console.log(url)
            const eventSource = new EventSource(url)
            eventSource.addEventListener('WAHAT', event => {
                let jsonStr = event.data.replace(/'/g, '"');
                console.log(`Back cказал: ${event.data}`);
                console.log(typeof(event.data));
                console.log(event);
                this.$emit("sse-event", JSON.parse(jsonStr))
            });

            //Здесь описываем запрос без сохранения, где читаем карту
            axios.post('https://localhost:8080/contract', {
                order_id: "822a3a17-5d5b-425e-af04-4a99a4d46229",
                user_id: "f96300f2-a492-4d0f-bb16-1ec9d163bbc3",
                card_number: "1234567890123456",
                card_expiry_year: "24",
                card_expiry_month: "10",
                card_csc: "666",
                card_cardholder: "IVAN IVANOV",
                amount_value: 1500.123,
                amount_currency: "RUB",
                method: "bank_card",
                save_payment_method: true,
                payment_method_id: ""
                
            })
            .then(response => {
                console.log(response.data);
            })
            .catch(error => {
                console.error(error);
            });
        },
    },
}
</script>

<style>
.item{
    display: flex;
    flex-direction: column;
    height: 400px;
    width: 400px;
}
input{
    height: 50px;
    color: black;
    border: 2px solid black;
    padding: 10px 15px;
    margin-top: 5px;
}
.btn{
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: black;
    color:white;
    height: 50px;
    width: 100px;
    margin-top: 30px;
}
.btn:hover{
    background-color: rgb(80, 80, 80);
}
.small_block{
    display: flex;
    justify-content: space-between;
    height: 50px;
}

.cvv{
    width: 100px;
    border-radius: 10px;
    height: 40px;
    margin-top: 30px;
}
.card_name{
    width: 190px;
}
.card_date{
    width: 190px;
}
</style>