<template lang="">

    

    <div class="">
        <div class="form-group">
            <label for="title">Title</label>
            <input v-model="title" id="title"  type="text" class="form-control"  />
        </div>
    
        <div class="form-group">
            <label for="image">image Url</label>
            <input v-model="image"  id="image"  type="text" class="form-control"  />
        </div>
    
        <div class="form-group">
            <label for="price">Price</label>
            <input v-model="price" id="price"  type="number" class="form-control"  />
        </div>

        <div class="form-group">
            <label for="category"></label>
                <select v-model="category" id="category" class="form-control">
                    <option :value="cat.id" v-for="cat in categories">{{ cat.name }}</option>
                </select>
            
        </div>
        
        <br />
        <button class="btn btn-dark" @click="addCar">Add Car</button>
        <br />

        <div id="well">
            title : {{ title }}
            image : {{ image }}
            price : {{ price }}
            category : {{ category }}
        </div>
    </div>



</template>


<script>
    export default {
        props:["toogle"],

        data(){

           return{
            toogle : false,
            title : '',
            image : '',
            price : '',
            categories : [
            {id: 1 , name: 'Ferrari'},
            {id: 2 , name: 'Volkswagen'}
            ],
            category: "2"

           }

        },
        methods: {
            addCar(){
                let title = this.$refs.title.value;
                let image = this.$refs.image.value;
                let price = this.$refs.price.value;

                if(title == "" || image =="" || price ==""){
                    return ;
                }
                const car = {
                    title : title,
                    image : image,
                    price : price
                }

                this.$emit('addCar', car);

                this.$refs.title.value = "";
                this.$refs.image.value = "";
                this.$refs.price.value = "";

            }
        },
    };
</script>


<style lang="">
</style>