<template>
    <div class="cart">
        <div class="container>
            <div>
                <div v-for= " (i, idx) in state.items" :key="idx">
                    <img :src="i.imgPath" />
                    <span class="name">{{i.name}}</span>
                    <span class="price">{{i.price}}</span>

        </div>
    </div>
</template>

<script>
import {reactive} from "vue";
import axios from "axios"


export default{
    setup(){
        const state = reactive({
            items:[]
        })

        axios.get("/api/cart/items").then(({data}) => {
            console.log("data", data);
            state.items = data;
        })




        return {state}
    }
}
</script>

<style scoped>
</style>
