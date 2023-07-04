<template>
        <!-- Вынести в отдельный компонент -->
        <div class="card-save btn"
            v-for="cardl in saveCardList" 
            :key="cardl.id"
            @click="send_pay_from_save(cardl.id)"
        > 
            <strong><code>**** {{ cardl.data.last4 }}</code></strong>
        </div>
</template>

<script>
import axios from 'axios';
export default {
    name: "save-card",
    props: {
        saveCardList: {
            type: Array,
            required: true,
        },
        card:{
            type: Object,
            required: true,
        },
        user_id: {
            type:String,
            required: true,
        }
    },
    methods:{
        send_pay_from_save(index){
            var uuidv4 = () => {
            return 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g, function(c) {
                var r = Math.random() * 16 | 0, v = c == 'x' ? r : (r & 0x3 | 0x8);
                return v.toString(16);
            })};
            let order = uuidv4()

            console.log({
                order_id: order,
                user_id: this.user_id,
                card_csc: String(this.card.card_cvv),
                amount_value: Math.random() * (2000.0 - 10.0) + 10.0,
                amount_currency: "RUB",
                payment_method_id: index
            });
            axios.post('http://localhost:80/api/contract', {
                order_id: order,
                user_id: this.user_id,
                card_csc: String(this.card.card_cvv),
                amount_value: Math.random() * (2000.0 - 10.0) + 10.0,
                amount_currency: "RUB",
                method:"bank_card",
                payment_method_id: index
            })
            .then(response => {
                console.log(response.data);
            })
            // .catch(error => {
            //     console.error(error);
            // });
        },
    }
}
</script>

<style>
</style>