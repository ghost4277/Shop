<template>
  <div class="slider_wrapper">
      <div class="slider">
          <div class="slider_items">
              <img src="@/assets/snikers.jpg" alt="" class="images"></div>
          <div class="slider_items">
              <img src="@/assets/clock.jpg" alt="" class="images"></div>
          <div class="slider_items">
              <img src="@/assets/Dodge.jpg" alt="" class="images"></div>
          <div class="slider_items">
              <img src="@/assets/gym.jpg" alt="" class="images"></div>
          <div class="slider_items">
              <img src="@/assets/phone.jpg" alt="" class="images"></div>
          <div class="slider_items">
              <img src="@/assets/ring.jpg" alt="" class="images"></div>
          <div class="slider_items">
              <img src="@/assets/sergi.jpg" alt="" class="images"></div>
          <div class="slider_items">
              <img src="@/assets/Statham.jpg" alt="" class="images"></div>
      </div>
      
      <button class="buttons right_btn">&#8592;</button>
      <button class="buttons left_btn">&#8594;</button>
  </div>
</template>

<script>
export default {

}
</script>

<style scoped>
.slider{
    display: flex;
    margin: 10px auto;
}
.slider_items{
    margin-left: 10px;
    border:1px solid black;
}
.images{
    width: 400px;
    height: 400px;
}
.buttons{
    background: #ff4747;
    border: 1px solid #ff4747;
    border-radius: 50%;
    width: 40px;
    height: 40px;
    color:white
}
.right_btn{
    position: absolute;
    left: 0;
    top: 280px;
}
.left_btn{
    position: absolute;
    right: 0;
    top: 280px;
}
</style>