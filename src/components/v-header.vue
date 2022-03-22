<template>
 <header>
   <div class="header__wrapper">
     <img class="logo" src="@/assets/logo.png" alt="">
     <div class="search__line">
       <form action="">
         <input type="text" placeholder="Ты это заходи если чё" class="line">
       </form>
       <button class="search__button"></button>
       <div>
     
      <v-basket :item="item" @delete="remove" />
       </div>
      
     </div>
   </div>
 </header>
</template>
<script>
import vBasket from "@/components/v-basket.vue";

export default {
  props:{
  item : Array
  },
  components: {
   vBasket
  },
  methods:{
   remove(vendorCode){
     console.log(vendorCode)
     this.$emit('delet',vendorCode)
      
    }
    }
  }


</script>
<style scoped>
    *{
  margin: 0px;
  padding: 0px;
}
.header__wrapper{
   display:flex;
  
  justify-content: space-between;
  width: 1000px;
  margin: 0 auto;
}
.search__line{
  display:flex;
  margin-top: 32px;
}
.logo{
  width: 200px;
  height: 100px;
}
.search__button{
  background-color: #ff4747;
  background-image: url(https://ae01.alicdn.com/kf/U076fc12af7c8408c9107c3e20c1fefd7G.png);
  background-position: 0 -1321px;
  background-repeat: no-repeat;
  border: 0;
  border-radius: 0 4px 4px 0;
  cursor: pointer;
  height: 36px;
  width: 40px;
}
.line{
  border-radius: 4px 0 0 4px;
    border-right: 0;
    border: 2px solid red;
    position: relative;
    display: block;
    width: 642px;
    padding: 7px 10px 7px 16px;
    line-height: 18px;
    font-size: 15px;
    box-sizing: border-box;
    outline: none;
    
}

</style>