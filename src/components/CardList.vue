<script>
import axios from 'axios';
import { store } from '../store.js';
import DetailCard from './DetailCard.vue';
export default {
    components:{
        DetailCard
    },

    data () {
        return {
            store 

        }
    },created() {
        this.getCards();
        this.getArchetypes();
        
    },
    
    methods:{
        getCards(){
            axios.get(store.apiUrl).then((response) => {
                store.CardList = response.data.data;
                store.loading = false;

            });
        },
        getArchetypes (){
            axios.get(store.apiArchetypesUrl).then((response) => {
                console.log (response.data); 

            });
        }

    }
    
}
</script>

<template lang="">
    <div class="container">
        <div class="row"> 

            <DetailCard v-for="card in store.CardList"  :key="card.id" :card="card"  />
           

        </div> 
    </div>
    
</template>

<style lang="scss" scoped>



</style>