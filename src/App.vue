<template>
  <v-header />
  <v-main />
  <footer>
    <p>СТЭТХЭМ </p>
    <p>ЛУЧШИЙ</p>
  </footer>
</template>

<script>
import vHeader from "@/components/v-header.vue";
import vMain from "@/components/v-main.vue";

export default {
  components: {
    vHeader,
    vMain,
  },
  
};
</script>

<style>
.carts {
  display: flex;
  flex-wrap: wrap;
}
footer{
  background: white;
  display: flex;
  justify-content: space-between;
}
</style>
