<template>
  <v-window :window="window" @closeWindow="window = !window" />
  <v-header :item="basketContainer" @delet="delet" />
  <main class="main">
    <v-slider/>
    <button @click="forfive" class="changer btn__for5" >5</button>
    <button @click="forthree" class="changer btn__for3">3</button>
    <div class="main__wrapper">
      <div class="carts">
        <v-products
          @add="add"
          v-for="product in products"
          :key="product"
          :product="product"
        />
      </div>
    </div>
    <div class="pagination">
      <span class="pagination_items first"> 1</span>
      <span class="pagination_items">2 </span>
      <span class="pagination_items"> 3</span>
      <span class="pagination_items"> 4</span>
      <span class="pagination_items"> 5</span>
      <span class="pagination_items"> 6</span>
      <span class="pagination_items"> 7</span>
      <span class="pagination_items"> 8</span>
    </div>
  </main>
  <footer>
    <p>СТЭТХЭМ</p>
    <p>ЛУЧШИЙ</p>
  </footer>
</template>

<script>
import vHeader from "@/components/v-header.vue";
import vProducts from "@/components/v-products.vue";
import VWindow from "@/components/v-window.vue";
import VSlider from "@/components/v-slider.vue";
export default {
  components: {
    vHeader,
    vProducts,
    VWindow,
    VSlider
  },
  data() {
    return {
      products: [
        // {
        // //   image: "snikers.jpg",
        // //   name: "Кросовки",
        // //   price: "3456",
        // //   sold: "31",
        // //   vendorCode: "A1",
        // // },
        // // {
        // //   image: "clock.jpg",
        // //   name: "Часы",
        // //   price: "3436",
        // //   sold: "42",
        // //   vendorCode: "A2",
        // // },
        // // {
        // //   image: "sergi.jpg",
        // //   name: "Серьги",
        // //   price: "3326",
        // //   sold: "32",
        // //   vendorCode: "A3",
        // // },
        // // {
        // //   image: "ring.jpg",
        // //   name: "Кольцо",
        // //   price: "6556",
        // //   sold: "56",
        // //   vendorCode: "A4",
        // // },
        // // {
        // //   image: "phone.jpg",
        // //   name: "Телефон",
        // //   price: "3431",
        // //   sold: "44",
        // //   vendorCode: "A5",
        // // },
        // // {
        // //   image: "Statham.jpg",
        // //   name: "Стэхэм",
        // //   price: "eror",
        // //   sold: "eror",
        // //   vendorCode: "A6",
        // // },
        // // {
        // //   image: "gym.jpg",
        // //   name: "Гантели",
        // //   price: "6236",
        // //   sold: "444",
        // //   vendorCode: "A7",
        // // },
        // // {
        // //   image: "Dodge.jpg",
        // //   name: "Машина",
        // //   price: "124214151256",
        // //   sold: "3",
        // //   vendorCode: "A8",
        // // },
      ],
      isLoading: true,
      basketContainer: [],
      window: false,
      changer: false
    };
  },
  methods: {
    add(product) {
      // console.log(this.basketContainer.vendorCode)
      // console.log(product.vendorCode)
      // if(this.basketContainer.vendorCode!==product.vendorCode){;
      // }
      const foundProduct = this.basketContainer.find(p => p.vendorCode === product.vendorCode)

      if (!foundProduct) {
        this.basketContainer.push({ ...product, quantity: 1 });
        return
      }
      foundProduct.quantity += 1
      console.log('Товар уже в корзине')
      console.log(foundProduct.quantity )


      // this.basketContainer.filter(function(item){

      //   if(product.vendorCode!=item.vendorCode)this.basketContainer.push(product);
      // })
      //       this.basketContainer = this.basketContainer.filter(function(it) {
      //         if (product)
      // });
      if (this.window == false) this.window = !this.window;
    },
    delet(vendorCode) {
      this.basketContainer = this.basketContainer.filter(
        (e) => e.vendorCode !== vendorCode
      );
    },
    closeWindow() {
      this.window = !this.window;
    },
    forfive(){
    this.changer=true
    },
    forthree(){

    },

  },
  created() {
    const productsPromise = fetch('https://fakestoreapi.com/products')

    productsPromise
      .then(response => response.json())
      .then(products => {
        this.products = products
      })
      .catch(err => {
        alert(err)
      })
      .finally(() => {
        this.isLoading = false
      })
  }

};
</script>

<style>
* {
  margin: 0px;
  padding: 0px;
}
.pagination{
  display: flex;
  margin: 10px auto;
  width: 151.1px;
  
}
.first{
  background: #ff4747;
  border-radius: 50%;
  border: 1px solid #ff4747;
  color: white;
}
.pagination_items{
  margin-left: 10px;
  cursor: pointer;
  transition: 0.5s;
  padding: 4px;
}
.pagination_items:hover{
  background: #ff4747;
  border-radius: 50%;
  border: 1px solid #ff4747;
  
  color: white;
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
.changer{
  position: relative;
 
}

footer {
  background: white;
  display: flex;
  justify-content: space-between;
}
</style>
