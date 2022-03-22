<template>
<div v-if="window">
    <p>Объект добавлен в корзину</p>
    <button @click="$emit('closeWindow')">Ок</button>
</div>
</template>
<script>
export default {
  props: {
    window: Boolean,
  },
  methods:{
      remove(){
          this.window==false
      }
  }
};
</script>
<style scoped>
div{
    position: absolute;
    margin: auto;
    border: 1px solid black;
    text-align: center;
    padding: 20px;
    background: white;
    border-radius: 10px;
}
button{
    padding: 5px;
    color: white;
    background: red;
    margin-top: 20px;
    border: none;
    width: 100px;
}
</style>