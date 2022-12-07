<template>
  <div class="container">
    <h1>Круги и квадраты, v 1.0</h1>
    <div class="header-wrapper">
      <div class="burger-wrapper">
        <div ref="burger"
          class="burger"
          @click="burgerMenu"
        >
          <div class="b1"></div>
          <div class="b2"></div>
          <div class="b3"></div>
        </div>
      </div>
      <div class="check-box-group-wrapper">
        <input class="check" type="checkbox" name="circle" id="" v-model="store.isCircle"><p>Круги</p>
        <input class="check" type="checkbox" name="" id="" v-model="store.isSquare"><p>Квадраты</p>
      </div>
    </div>
  </div>
</template>

<script>
import store from "../store"
export default {
  name: 'Header',
  data(){
    return{
      store,
    }
  },
  methods: {
    burgerMenu () {
      this.$refs.burger.classList.toggle("change");
      window.leftMenu.classList.toggle("no-display")
      console.log(window.leftMenu)
    }
  }
}
</script>
<style scoped>
.container{
  padding: 60px 5% 0;
  position: sticky;
  top:0;
  background-color: #fff;
}
.header-wrapper {
  display: flex;
}
.burger-wrapper {
  width: 30%;
}
.burger {
  cursor: pointer;
}
.b1,
.b2,
.b3 {
  width: 36px;
  height: 5px;
  background-color: #000;
  margin: 5px 0;
  transition: 0.3s;
}
.change .b1 {
  transform: rotate(-45deg) translate(-9px, 6px);
}
.change .b3 {
  transform: rotate(45deg) translate(-9px, -6px);
}
.change .b2 {
  opacity: 0;
}
.check-box-group-wrapper {
  width: 70%;
  display: flex;
  justify-content: start;
}
.check-box-group-wrapper p{
  font-weight: bold;
}
.check{
  zoom: 1.5;
  margin-left: 20px;
}
</style>