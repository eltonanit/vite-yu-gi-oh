<script>
import axios from 'axios';
import { store } from '../store.js';
export default {

    data () {
        return {
            store 

        }
    },created() {
        this.getCards()
        
    },
    
    methods:{
        getCards(){
            axios.get(store.apiUrl).then((response) => {
                store.CardList = response.data.data;

            });
        }

    }
    
}
</script>

<template lang="">
    <div class="container">
        <div class="row"> 
            <div class="col-20" v-for="card in store.CardList" :key="card.id">
                {{card.name}}
                
            </div> 

        </div> 
    </div>
    
</template>

<style lang="">


</style>