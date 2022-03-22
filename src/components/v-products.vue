<template>
  <div class="cart">
    <img :src="require('../assets/' + product.image)" alt="" />
    <div class="cart__text">
      <p>{{ product.name }}</p>
      <p>Цена:{{ product.price }}</p>
      <p>Проданно:{{ product.sold }}</p>
      <v-switcher :val="1" />
      <button @click.prevent="$emit('add', this.product)" class="basket__add">
        Добавить в корзину
      </button>
    </div>
  </div>
</template>

<script>
import VSwitcher from "@/components/v-switcher.vue";

export default {
  components:{
      VSwitcher
  },
  props: {
    product: Object,
  },
};
</script>

<style scoped>
.cart {
  margin: 10px 10px;
  width: 15%;
  height: 300px;
  border: 1px solid gray;
  border-radius: 10px;
  background-color: #ffffff;
  text-align: center;
  position: relative;
}
.cart img {
  max-width: 130px;
  max-height: 130px;
}
.basket__add {
  color: white;
  background-color: #ff4747;
  border: none;
  cursor: pointer;
  padding: 10px;
}
.cart__text {
  position: absolute;
  bottom: 30px;
  margin-left: 30px;
}
</style>