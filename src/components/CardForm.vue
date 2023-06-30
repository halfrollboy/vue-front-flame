<template>
<form class="item" @submit.prevent>

    <!-- Вынести в отдельный компонент -->
    <div class="card-save btn" 
        v-for="cardl in saveCardList" 
        :key="cardl.id"
        @click="send_pay_from_save(cardl.id)"
    > 
        <strong><code>**** {{ cardl.data.last4 }}</code></strong>
    </div>
    <!-- v-for="eventl in eventslist" :key="eventl.id">{{ eventl.body }}  -->

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
            maxlength=3>
        <span class="div-check">
            <input 
                style="width: 25px; 
                height: 25px;" 
                type="checkbox" 
                id="scales" 
                name="save"
                v-model="card.save"
                >
            <label for="save">Save card</label>
        </span>
    </div>
    <div class="btn"
        @click="get_message_from_back"
        >PAY</div>

</form>
</template>

<script>
import axios from 'axios';
export default {
    emits: ['sse-event'],
    props:{
        saveCardList:{
            type: Array,
            required: true,
        },
        user_id: String
    },
    data(){
        return{
            card:{
                id: 0,
                card_number:'5555 5555 5555 4444',
                card_holder:'Taran Yurij',
                card_data:'10/23',
                card_cvv:'666',
                save: false
            }
            
        }
    },
    methods:{
        sendForm(e){
            // this.post.id = Date.now()
            // this.card.card_number
            console.log("[eq]",e)
        },
        send_pay_from_save(index){
            var uuidv4 = () => {
            return 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g, function(c) {
                var r = Math.random() * 16 | 0, v = c == 'x' ? r : (r & 0x3 | 0x8);
                return v.toString(16);
            })};
            let order = uuidv4()

            console.log(index);
            axios.post('https://localhost:8080/contract', {
                order_id: order,
                user_id: this.user_id,
                card_csc: this.card.card_cvv,
                amount_value: Math.random() * (2000.0 - 10.0) + 10.0,
                amount_currency: "RUB",
                method: "bank_card",
                save_payment_method: false,
                payment_method_id: index
            })
            .then(response => {
                console.log(response.data);
            })
            .catch(error => {
                console.error(error);
            });
        },
        get_message_from_back() {

            var uuidv4 = () => {
            return 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g, function(c) {
                var r = Math.random() * 16 | 0, v = c == 'x' ? r : (r & 0x3 | 0x8);
                return v.toString(16);
            })};
            let order = uuidv4()
            var url = 'http://localhost:8084/sse/sse/' + order +'/'+ this.user_id
            
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
            axios.post('http://localhost:8082/contract', {
                order_id: order,
                user_id: this.user_id,
                card_number: this.card.card_number,
                card_expiry_year: "24",
                card_expiry_month: "10",
                card_csc: this.card.card_cvv,
                card_cardholder: this.card.card_holder,
                amount_value: Math.random() * (2000.0 - 10.0) + 10.0,
                amount_currency: "RUB",
                method: "bank_card",
                save_payment_method: this.card.save,
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
/* .save-card{
    display: flex;
    flex-direction: column;
    height: 400px;
    width: 400px;
} */
.card-save{
    display: flex;
    align-self: flex-end;
    width: 200px;
    display: flex;
    border-radius: 20px;
    text-align: center;
    padding-top: 15px;
    padding-bottom: 15px;
    margin-bottom: 15px;
    margin-top: 0px;
    background-color: rgb(212, 212, 212);
    color: black;
    font-size: 15px;
}
.div-check{
    display: flex;
    height: 20px;
    width: 120px;
    text-align: center;
    padding-top: 30px;
}
.div-check .label{
    padding: 40px;  
}
</style>