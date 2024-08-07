<script>
import axios from 'axios';
import { store } from '../store.js';
import DetailCard from './DetailCard.vue';
import FilterCards from './FilterCards.vue';

export default {
    components:{
        DetailCard,
        FilterCards
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
               
                for(let i=0; i<10; i++) {
                    store.archetypesList.push(response.data[i]);
                }               

            });
        }

    }
    
}
</script>

<template lang="">
    <div class="row">
        <FilterCards />
        <div class="row"> 

            <DetailCard v-for="card in store.CardList"  :key="card.id" :card="card"  />
           

        </div> 
    </div>
    
</template>

<style lang="scss" scoped>



</style>