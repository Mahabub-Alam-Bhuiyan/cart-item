<template>
  <div id="app">


 <navbar @search="search" ></navbar>


<div class="container marketting">
  <div class="row">
   <div class="col-sm-9">
  <Inventory @newitemadded="AddToCart" :items="items" ></Inventory>
        </div>
    <div class="col-sm-3">
  <cart :items="cart" ></cart>
        </div>
  </div>
</div>

  </div>
</template>

<script>

import Navbar from './components/Navbar'
import Inventory from "./components/Inventory";
import Cart from './components/Cart.vue';
import data from './data.js'


export default {
 components: {
   Navbar,
   Inventory,
   Cart
 },
  data(){
   return {
     message: 'Hello Vue.js!',

     items : [ ],
     cart: [
       {
         id: 1,
         title : "Ferrari",
         photo:"http://dummyimage.com/250x250.png/ff4444/ffffff",
         price: 80.50

       }
     ]
   }
  },

  mounted() {
   this.items = data
  },
  methods:{
    search(keyword){
      this.items = data.filter(item => {
        return item.title.toLowerCase().indexOf(keyword.toLowerCase()) !== -1
      } )
    },
  AddToCart(item){
     this.cart.push(item)
   },
    reverseMessage: function () {
      this.message = this.message.split('').reverse().join('')
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.marketting{
  padding: 10px 0;
}
</style>
