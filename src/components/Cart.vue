<template>
   <ul class="list-group">
        <li class="list-group-item">
          <span class="item-name">Name</span>
           <span class="item-price float-right">Price</span>
        </li>
     <li class="list-group-item" v-for="(item,index) in items" :key="index">
      <button @click="removeitem(index)" class="btn btn-danger btn-sm" >-</button>
      <span class="item-name">{{ item.title }}</span>
      <span class="item-price float-right ">{{ item.price }}</span>
    </li>
     <li class="list-group-item">
          <span class="item-name">Total</span>
          <span class="item-price float-right">{{ totalprice }}</span>
     </li>
      </ul>
</template>

<script>
export default {
    props: ['items'],
    computed:{
        totalprice(item){
            var total = 0;
            this.items.forEach(item => {
                total += parseFloat(item.price)
            });
            return total;
        }
    },
    methods:{
        removeitem(index){
            this.items.splice(index,1)
        }
    }
}
</script>

<style>
.list-group-item{
  margin-bottom: 10px;
}
</style>
