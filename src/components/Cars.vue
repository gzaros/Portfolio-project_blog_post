<template lang="">

  <div class="row" v-if="toogle">
    <div class="col-md-6 mx-auto">
      <AddCars  @addCar="addCar($event)" />
    </div>
  </div>



  <div class="row">
    <div class="col-md-6">

      <nav aria-label="breadcrumb">
        <slot></slot>
      </nav>

      <h4>List of Cars</h4>
    </div>

    <div class="col-md-6 d-flex align-items-start justify-content-end">
         <button 
            class="btn btn-sm btn-success"
            :class="{'bg-succes': !toogle , 'bg-dark': toogle}"
            @click="showForm()">
            {{ toogle ? 'Close' : 'New' }}
         </button>
    </div>

  </div>


  <div class="row">
    <div class="row row-cols-1 row-cols-md-2 g-4">
      <div class="col col-md-4" v-for="car in cars">
        <OneCarVue :car="car" @delete="deleteOneCar($event)" />
      </div>

    </div>

  </div>

  <teleport to='#alert' v-if="carDeleted" >

    <div class="alert alert-danger text-center" role="alert">
      <strong>Car is deleted</strong>
    </div>  
    
  </teleport>

  <teleport to='#alert' v-if="carAdded" >

    <div class="alert alert-success text-center" role="alert">
      <strong>Car is Added</strong>
    </div>  
    
  </teleport>

  



</template>


<script>
import OneCarVue from "./OneCar";
import AddCars from "./AddCars";
export default {
  components: {
    OneCarVue,
    AddCars
  },

  data() {
    return {
      carDeleted: false,
      carAdded : false,
      toogle :  false,
      cars: [
        {
          id: 1,
          title: "Honda Unveils Futuristic EV",
          image:
            "https://www.autogeeknation.com/wp-content/uploads/2024/01/Honda-Space-Hub-1024x576.png",
          price: 500,
        },
        {
          id: 2,
          title: "Ferrari’s Bold Leap",
          image:
            "https://www.autogeeknation.com/wp-content/uploads/2023/12/Ferrari-Purosangue-1024x576.png",
          price: 250,
        },
        {
          id: 3,
          title: "Porsche Panamera 2024",
          image:
            "https://www.autogeeknation.com/wp-content/uploads/2023/11/porsche-panamera-1024x576.png",
          price: 360,
        },
      ],
    };
  },

  methods: {
    deleteOneCar(id) {
      this.cars = this.cars.filter((car) => car.id != id);
      this.carDeleted = true;
      setTimeout(() => {
         this.carDeleted = false;
      }, 3000);

    },

    addCar(car){
      //this.cars.unshift(car);
      this.cars = [car, ...this.cars];
      this.toogle = false;
      this.carAdded = true;
      setTimeout(() => {
         this.carAdded = false;
      }, 3000);

    },
    showForm(){
      this.toogle = !this.toogle;
    }
  },
};
</script>


<style scoped>
h4 {
  color: rgb(81, 3, 73);
}
</style>