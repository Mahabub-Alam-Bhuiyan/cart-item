<template>
<div class="row">
  <div v-for="(item, index) in items" :key="index" class="card" style="width: 12rem;">
  <img class="card-img-top" :src="item.photo" alt="Card image cap">
  <div class="card-body">
    <h5 class="card-title">{{ item.title }}</h5>
    <p class="card-text">{{ item.price }}</p>
    <a @click="additem(item)" class="btn btn-primary">+add cart</a>
  </div>
</div>

</div>  
</template>

<script>
export default {
   props:['items'],
   methods:{
    additem(item){
      this.$emit("newitemadded",item)
    }
  }
}
</script>

<style>
.card{
    padding:0 5px;
}
</style>