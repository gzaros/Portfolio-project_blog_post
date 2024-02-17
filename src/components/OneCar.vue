<template lang="">
    
    
      <div class="card">
        <img :src="car.image" class="card-img-top" alt="{{ car.title }}">
        <div class="card-body">
          <h5 class="card-title">{{ car.title }}</h5>
          <span class="badge bg-primary">{{ car.price }} MAD</span>
          <div style="margin-top:5px;"></div>
          <button class="btn btn-sm btn-danger" @click="deleteOne(car.id)">delete</button>
        </div>
      </div>
    

</template>


<script>
export default {
    props:["car"],

    methods:{
        deleteOne(id){
          
          this.$emit('delete', id)
        }
    }
    
}
</script>


<style lang="">
    
</style>