<template>
<div>

    <!-- <div class="start" :class="{ end : modal_status }">
    <Modal :modal_status = "modal_status"
       :product="product"
       :click_product="click_product"
       @close_modal = "modal_status=$event"
       />
      </div> -->

  <transition name="fade" >
    <Modal :modal_status = "modal_status"
       :product="product"
       :click_product="click_product"
       @close_modal = "modal_status=$event"
       />
  </transition>

  <div class="menu">
    <a v-for="(for_te, i) in menu" :key="i">{{(i+1)+'\t'}}{{for_te}}</a>
  </div>

  <Discount v-if="showDiscount == true" :obj="obj" :amount="amount"/>


  <button @click="resetSort">되돌리기</button>
  <button @click="priceSort">가격순 정렬</button>

    <!-- <span>{{ num[0] }}</span>
    <button @mouseover="increase">+1 button</button> -->

  <Card
    @openModal="modal_status=true; click_product=$event"
    v-for="(for_te, i) in product" :key="i"
    :product = "product[i]"
     />

</div>
</template>

<script>

import data from './oneroom.js';
import Discount from './Discount.vue';
import Modal from './Modal.vue';
import Card from './Card.vue';


export default {
  name: 'App',
  data(){
    return{
      obj: {name:'kim', age:25},
      menu: ['Home','Shop','About'],

      product_origin: [...data],
      product: data,

      click_product:0,
      num: [0,0,0],
      color:'color:blue',
      modal_status: false,

      showDiscount: true,
      amount : 100,
    }
  },
  methods:{
    increase(){
      this.num[0]++;
    },
    resetSort(){
      this.product = [...this.product_origin];
    },
    priceSort(){
      this.product.sort(function(a,b){
        return a.price-b.price
      })
    },
    
  },

  mounted() {
    // setTimeout(() => {
    //   this.showDiscount = false;
    // },2000);
    
    setInterval(() => {
      if(this.amount > 0)
        this.amount--;
    }, 100);
  },
  components: {
    Discount : Discount,
    Modal : Modal,
    Card : Card,
  }
}
</script>





<style>

body{
  margin:0;
}
div{
  box-sizing: border-box;
}
.black_bg{
  width:100%; height: 100%;
  background : rgba(0,0,0,0.5);
  position: fixed; 
  padding: 20px;
}
.white_bg{
   width:100%;
   background :white;
   border-radius: 8px;
   padding: 20px;
}

.fade-enter-from{
  transform: translateY(-1000px);
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
    transform: translateY(0px);
}

.fade-leave-from{
  opacity: 1;
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  opacity: 0;
}

.start{
  opacity: 0;
  transition: all 1s;
}
.end{
  opacity: 1;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu{
  background : blueviolet;
  padding : 15px;
  border-radius: 5px;
}
.menu a{
  color:white;
  padding:10px;
}
.test_img{
  width: 100%;
}

.discount{
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
</style>
