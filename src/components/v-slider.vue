<template>
  <div class="slider_wrapper">
    <div v-for="item in slider" :key="item.id">
      <img
        :style="{ right: 100 * curentSlide + '%' }"
        class="image"
        :src="item.image"
        alt=""
      />
    </div>
    <button @click="next" class="buttons next">&#8594;</button>
    <button @click="prev" class="buttons prev">&#8592;</button>
    <!-- 
&#8592; -->
  </div>
</template>

<script>

export default {
  data() {
    return {
        curentSlide:0,
    };
  },
 
  props: {
    slider: Array,
    interval: Number
  },
  methods: {
    next() {
        if(this.curentSlide>this.slider.length-7)this.curentSlide=0
        else this.curentSlide++
        
        console.log(this.curentSlide)
    },
    prev() {
        if(this.curentSlide>0)this.curentSlide--
        
        console.log(this.curentSlide)

    },
    mounted(){
      if(this.interval>0){
          let vm=this;
          setInterval(  function(){
              vm.next()
              
          }, vm.interval)
      }
  }
  },
  
};
</script>

<style scoped>
.image {
  width: 300px;
  height: 300px;
  position: relative;
  transition: 0.7s;
}
.slider_wrapper {
  display: flex;
  margin: 10px auto;
  max-width: 2000px;
  overflow: hidden;
}
.buttons {
  background: #ff4747;
  border: 1px solid #ff4747;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  color: white;
  position: absolute;
  top: 250px;
}
.next {
  right: 0;
}
</style>