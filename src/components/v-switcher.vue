<template>
  <div class="switcher">
    <button @click="swichUp" class="buttons plus">+</button>
    <input class="value" type="text" :value="value" />
    <button @click="swichDown" class="buttons minus">-</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
        value: null,
    }
  },

  props: {
    val: Number,
  },

  methods: {
    swichUp() {
      this.value++;
       this.$emit('up')
    },
    swichDown() {
      this.value--;
      if (this.value < 1) this.value = 1;
       this.$emit('down')
    },
  },

  created() {
      this.value = this.val
  },
};
</script>

<style scoped>
.switcher {
  display: flex;
  justify-content: space-between;
  margin: 5px 0;
}
.buttons {
  color: white;
  background: #ff4747;
  border: none;
  padding: 5px 0px;
  text-align: center;
  width: 54px;
  cursor: pointer;
}
.value {
  width: 30px;
  text-align: center;
}
</style>