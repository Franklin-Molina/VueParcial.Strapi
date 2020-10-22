<template >
  <!--  -->


  

  <div class="container mt-4">
    <div class="row">
      <div class="col-12"></div>
    </div>

    <div class="row">
      <div
        class="col-12 col-sm-12 col-md-6 col-lg-4"
        v-for="items in imagenes"
        :key="items.id"
      >
        <Imagen :items="items" />
      </div>
    </div>
  </div>
</template>
<script>
import Imagen from "../components/Prueba.vue";

export default {
  name: "Home",
  components: { 
    Imagen 
    },
  data() {
    return {
      imagenes: [],
    };
  },
  mounted() {

    
    fetch("http://localhost:1337/imagenes")
      .then((res) => res.json())
      .then((data) => {
        console.log(data);
        this.imagenes = data;
      });
  },


  
};



</script>
<style >
#col_border {
  text-decoration: none;
}
h1 {
  color: rgb(0, 0, 0);
  text-align: center;
}

.color {
  background: black;
}

.btnhome {
    font-family: Lato, sans-serif;
  text-decoration: none;
width: 1550px;
  border: 5px solid #2c3e50;
  color: #2c3e50;
  display: block;
 
  font-size: 2rem;
  letter-spacing: 0.1rem;
  padding: 1rem;
  position: relative;
  text-decoration: none;
  text-transform: uppercase;
}

.btnhome::before {
  content: "";
  background-color: #E26A6A;
  box-shadow: 10px 10px 0 #F1C40F, 
              20px 20px 0 #3498DB;
  position: absolute;
  left: 0.25rem;
  top: 0.5rem;
  height: 102%;
  width: 102%;
  z-index: -1;
  transition: all 0.4s ease;
}

.btnhome:hover::before {
  box-shadow: none;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
}


</style>