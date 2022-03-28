<template>
  <button @click="basketVisablee" class="basket"></button>
  <div class="basket__counetr">{{ item.length }}</div>
  <div v-if="basketVisable" class="basket__wtapper">
    <div v-if="!isEmpty" class="empty">Здесь пока нет эллементов</div>
    <div v-else>
      <div class="basket__items" v-for="p in item" :key="p.id">
        <img :src="p.image" alt="" />
        <v-switcher @up="up" :val="p.quantity" class="switcher" />
        <span>{{ p.name }}</span>
        <span>{{ p.price }}</span>
        <button @click="deleteFromBasket(p.id)">Удалить</button>
      </div>
    </div>
  </div>
</template>

<script>
import VSwitcher from "@/components/v-switcher.vue";
export default {
  components: {
    VSwitcher,
  },
  data() {
    return {
      basketVisable: false,
    };
  },
  props: {
    item: Array,
  },
  computed: {
    isEmpty() {
      return this.item.length !== 0;
    },
    // up(){
    //   console.log(this.item.quantity);
    //   return this.item.quantity
    // }
  },
  methods: {
    basketVisablee() {
      this.basketVisable = !this.basketVisable;
    },
    deleteFromBasket(vendorCode) {
      this.$emit("delete", vendorCode);
    },
    up(){
      console.log(this.item.quantity);
    }
  },
};
</script>

<style scoped>
.switcher {
  margin: auto 0;
  height: 25%;
}
.basket {
  display: block;
  width: 35px;
  height: 35px;
  border: none;
  background-color: white;
  background-image: url(https://ae01.alicdn.com/kf/U076fc12af7c8408c9107c3e20c1fefd7G.png);
  background-position: 0 -2895px;
  background-repeat: no-repeat;
  color: white;
  text-decoration: none;
  position: relative;
  left: 25px;
  cursor: pointer;
}
.basket__counetr {
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
.basket__wtapper {
  border: 2px solid black;
  border-radius: 10px;
  background-color: white;
  z-index: 100;
  position: absolute;
  left: 1170px;
  top: 90px;
  max-height: 500px;
  overflow: auto;
}
.basket__items {
  background-color: white;
  margin: 10px;
  height: 100px;
  width: 600px;
  border: 1px solid black;
  border-radius: 5px;
  display: flex;
  justify-content: space-between;
  text-align: center;
}
.empty {
  text-align: center;
  border: 1px solid black;
  padding: 35px 0px;
  width: 600px;
}
</style>