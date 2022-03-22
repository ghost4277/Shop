<template>
  <div class="switcher">
      <button @click="swichUp" class="buttons plus">+</button>
      <input class="value" type="text" :value="val">
      <button @click="swichDown" class="buttons minus">-</button>
  </div>
</template>

<script>
export default {
data(){
    return{
        val:1
    }
},
methods:{
    swichUp(){
        this.val++
    },
    swichDown(){
        this.val--
        if(this.val<1)this.val=1
    }
}
}
</script>

<style scoped>
.switcher{
    display: flex;
    justify-content: space-between;
    margin: 5px 0;
}
.buttons{
    color: white;
    background: #ff4747;
    border: none;
    padding: 5px 0px;
    text-align: center;
    width: 54px;
    cursor: pointer;
}
.value{
    width: 30px;
    text-align: center;
}
</style>