<template>
  <v-header />
  <v-main />
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

</style>
