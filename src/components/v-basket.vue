<template>
<div @click="basketVisable = !basketVisable" class="basket__counetr">{{counter}}</div>
<div v-if="basketVisable" class="basket__wtapper">
    <div  class="basket__items">
        <img src="@/assets/snikers.jpg" alt="">
        <span>name</span>
        <span>price</span>
    </div>
</div>
</template>

<script>
export default {
    data(){
        return{
            counter:0,
            basketVisable:false
        }
    },
    methods:{
        addInBasket(){
            this.counter=this.counter++
        }
    }
}
</script>

<style scoped>
.basket__counetr{
    background: #ff4747;
    width: 17px;
    height: 17px;
    border-radius: 50%;
    color: white;
    text-align: center;
    position: absolute;
    top: 30px;
    left: 1476px;
}
.basket__wtapper{
    border: 2px solid black;
    border-radius: 10px;
    background-color: white;
    display: inline-block;
    position: fixed;
    left: 1170px;
    top: 90px;
}
.basket__items{
    background-color: white;
    margin: 10px;
    height: 100px;
    width: 700px;
    border: 1px solid black;
    border-radius: 5px;
    display: flex;
    justify-content: space-between;
    
}
</style>