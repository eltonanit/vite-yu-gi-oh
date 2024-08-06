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
        <div class="card"> 
            <img :src="card.card_images[0].image_url" />
            <div class="card-body">
                <h3> {{card.name}} </h3>

                


                
            </div>  </div> 
               </div> 

        </div> 
    </div>
    
</template>

<style lang="scss" scoped>
.card {
    background-color: white;
    margin: 10px;
    img {
        max-width: 100%;
    }

}


</style>