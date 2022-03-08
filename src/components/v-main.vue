<template>
  <main class="main">
    <div class="main__wrapper">
      <div class="carts">
        <v-products v-for="product in products" :key="product" :product="product" />
      </div>
    </div>
    <v-basket/>
  </main>
</template>

<script>
import vProducts from "@/components/v-products.vue";
import vBasket from "@/components/v-basket.vue";

export default {
  components: {
    vProducts,
    vBasket
  },
  data() {
    return {
      
      products: [
        { image: "snikers.jpg", name: "Кросовки", price: "3456", sold: "31" },
        { image: "clock.jpg", name: "Часы", price: "3436", sold: "42" },
        { image: "sergi.jpg", name: "Серьги", price: "3326", sold: "32" },
        { image: "ring.jpg", name: "Кольцо", price: "6556", sold: "56" },
        { image: "phone.jpg", name: "Телефон", price: "3431", sold: "44" },
        { image: "Statham.jpg", name: "Стэхэм", price: "eror", sold: "eror" },
        { image: "gym.jpg", name: "Гантели", price: "6236", sold: "444" },
        { image: "Dodge.jpg", name: "Машина", price: "124214151256", sold: "3" },
      ],
    };
  },
};
</script>

<style scoped>
* {
  margin: 0px;
  padding: 0px;
}
.main {
  height: 3000px;
  background-color: #f2f2f2;
  width: 100%;
}

.carts {
  display: flex;
  flex-wrap: wrap;
  max-width: 1300px;
  margin-left: 450px;
}
</style>