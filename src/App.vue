<template>
  <v-window :window="window" @closeWindow="window = !window" />
  <v-header :item="basketContainer" @delet="delet" :products="products" />
  <main class="main">
    <v-slider 
    :slider="products"
    :interval="1000"/>
    <button @click="changer= true"  class="changer btn__for5">5</button>
    <button @click="changer= false "  class="changer btn__for3">3</button>
    <div class="main__wrapper">
      <div v-if="isLoading" class="loader">Loading...</div>
      <div  v-else class="carts">
        <v-products
        :class="changer ? 'big' : 'smale' "
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
    VSlider,
  },
  data() {
    return {
      products: [],
      isLoading: true,
      basketContainer: [],
      window: false,
      changer: false,
    };
  },
  methods: {
    add(product) {
      const foundProduct = this.basketContainer.find(
        (p) => p.id === product.id
      );

      if (!foundProduct) {
        this.basketContainer.push({ ...product, quantity: 1 });
        return;
      }
      foundProduct.quantity += 1;

      if (this.window == false) this.window = !this.window;
    },
    delet(id) {
      this.basketContainer = this.basketContainer.filter((e) => e.id !== id);
    },
    closeWindow() {
      this.window = !this.window;
    },
    forfive() {
      this.changer = true;
    },
    forthree() {},
  },
  created() {
    const productsPromise = fetch("https://fakestoreapi.com/products");

    productsPromise
      .then((response) => response.json())
      .then((products) => {
        this.products = products;
      })
      .catch((err) => {
        alert(err);
      })
      .finally(() => {
        this.isLoading = false;
      });
  },
};
</script>

<style>
* {
  margin: 0px;
  padding: 0px;
}
.big{
  width: 25%;
  transition: 1s;
}
.smale{
  width: 15%;
  transition: 1s;
}
.loader {
  color:  #ff0000;
  font-size: 90px;
  text-indent: -9999em;
  overflow: hidden;
  width: 1em;
  height: 1em;
  border-radius: 50%;
  margin: 72px auto;
  position: relative;
  -webkit-transform: translateZ(0);
  -ms-transform: translateZ(0);
  transform: translateZ(0);
  -webkit-animation: load6 1.7s infinite ease, round 1.7s infinite ease;
  animation: load6 1.7s infinite ease, round 1.7s infinite ease;
}
@-webkit-keyframes load6 {
  0% {
    box-shadow: 0 -0.83em 0 -0.4em, 0 -0.83em 0 -0.42em, 0 -0.83em 0 -0.44em, 0 -0.83em 0 -0.46em, 0 -0.83em 0 -0.477em;
  }
  5%,
  95% {
    box-shadow: 0 -0.83em 0 -0.4em, 0 -0.83em 0 -0.42em, 0 -0.83em 0 -0.44em, 0 -0.83em 0 -0.46em, 0 -0.83em 0 -0.477em;
  }
  10%,
  59% {
    box-shadow: 0 -0.83em 0 -0.4em, -0.087em -0.825em 0 -0.42em, -0.173em -0.812em 0 -0.44em, -0.256em -0.789em 0 -0.46em, -0.297em -0.775em 0 -0.477em;
  }
  20% {
    box-shadow: 0 -0.83em 0 -0.4em, -0.338em -0.758em 0 -0.42em, -0.555em -0.617em 0 -0.44em, -0.671em -0.488em 0 -0.46em, -0.749em -0.34em 0 -0.477em;
  }
  38% {
    box-shadow: 0 -0.83em 0 -0.4em, -0.377em -0.74em 0 -0.42em, -0.645em -0.522em 0 -0.44em, -0.775em -0.297em 0 -0.46em, -0.82em -0.09em 0 -0.477em;
  }
  100% {
    box-shadow: 0 -0.83em 0 -0.4em, 0 -0.83em 0 -0.42em, 0 -0.83em 0 -0.44em, 0 -0.83em 0 -0.46em, 0 -0.83em 0 -0.477em;
  }
}
@keyframes load6 {
  0% {
    box-shadow: 0 -0.83em 0 -0.4em, 0 -0.83em 0 -0.42em, 0 -0.83em 0 -0.44em, 0 -0.83em 0 -0.46em, 0 -0.83em 0 -0.477em;
  }
  5%,
  95% {
    box-shadow: 0 -0.83em 0 -0.4em, 0 -0.83em 0 -0.42em, 0 -0.83em 0 -0.44em, 0 -0.83em 0 -0.46em, 0 -0.83em 0 -0.477em;
  }
  10%,
  59% {
    box-shadow: 0 -0.83em 0 -0.4em, -0.087em -0.825em 0 -0.42em, -0.173em -0.812em 0 -0.44em, -0.256em -0.789em 0 -0.46em, -0.297em -0.775em 0 -0.477em;
  }
  20% {
    box-shadow: 0 -0.83em 0 -0.4em, -0.338em -0.758em 0 -0.42em, -0.555em -0.617em 0 -0.44em, -0.671em -0.488em 0 -0.46em, -0.749em -0.34em 0 -0.477em;
  }
  38% {
    box-shadow: 0 -0.83em 0 -0.4em, -0.377em -0.74em 0 -0.42em, -0.645em -0.522em 0 -0.44em, -0.775em -0.297em 0 -0.46em, -0.82em -0.09em 0 -0.477em;
  }
  100% {
    box-shadow: 0 -0.83em 0 -0.4em, 0 -0.83em 0 -0.42em, 0 -0.83em 0 -0.44em, 0 -0.83em 0 -0.46em, 0 -0.83em 0 -0.477em;
  }
}
@-webkit-keyframes round {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(360deg);
    transform: rotate(360deg);
  }
}
@keyframes round {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(360deg);
    transform: rotate(360deg);
  }
}
.pagination {
  display: flex;
  margin: 10px auto;
  width: 151.1px;
}
.first {
  background: #ff4747;
  border-radius: 50%;
  border: 1px solid #ff4747;
  color: white;
}
.pagination_items {
  margin-left: 10px;
  cursor: pointer;
  transition: 0.5s;
  padding: 4px;
}
.pagination_items:hover {
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
.changer {
  position: relative;
}

footer {
  background: white;
  display: flex;
  justify-content: space-between;
}
</style>
