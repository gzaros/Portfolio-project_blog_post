<template>
  <Header />

  <div class="container">
    
        
        
        <br />
        <Cars>

          <ol class="breadcrumb">
            <li class="breadcrumb-item"><a href="#">Home</a></li>
            <li class="breadcrumb-item active" aria-current="page">List of Cars</li>
          </ol>

          <template v-slot:btn-right>
              
          </template>
          

        </Cars>

        

    <br />
    <Footer title="© 2024 AutoGeekNation, Inc" href="https://www.AutoGeekNation.com" />

  </div>

  
</template>

<script>
import Header from "./components/Header";
import Cars from "./components/Cars";
import Footer from "./components/Footer";

export default {
  name: "App",
  components: {
    Header,
    Cars,
    Footer
  },
  data() {
    return {
      message: "goood",
    };
  },
  methods: {
    
  },
};
</script>

<style>


</style>
