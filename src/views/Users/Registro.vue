<template>
  <div>
    <h1>Registro</h1>
    <form @submit.prevent="register">
      <label for="username">Usuario</label>
      <strong style="color: red"> * </strong>
      <input type="text" v-model="username" required /> <br />

      <label for="nombre">Nombre </label>
      <strong style="color: red"> * </strong>
      <input type="text" v-model="nombre" required /><br />
      <label for="email">Email </label> <strong style="color: red"> * </strong>
      <input type="email" v-model="email" required /><br />
      <label for="password">Password </label>
      <strong style="color: red"> * </strong>
      <input type="password" v-model="password" required /><br />

      <div v-if="error">
        <div  class="mt-4 alert alert-danger alert-dismissible fade show" role="alert" >
          <strong>Error !</strong> Usuario / Correo ya existe!
          <button
            type="button"
            class="close"
            data-dismiss="alert"
            aria-label="Close"
          >
            <span aria-hidden="true">&times;</span> <br />
          </button>
        </div>
      </div>

        <div v-if="loading">
           <div  class="mt-4 alert alert-success alert-dismissible fade show" role="alert" >
          <strong> Exito !</strong> Se registro Exitosamente!
          <button
            type="button"
            class="close"
            data-dismiss="alert"
            aria-label="Close"
          >
            <span aria-hidden="true">&times;</span> <br />
          </button>
        </div>

      </div>
    

      <button type="submit">Registrar</button>
    </form>
    <div id="mensaje"></div>
  </div>
</template>

<script>


import axios from "axios";

var mensaje = document.getElementById('mensaje');
export default {
  name: "Registro",
  data() {
    return {
      username: "",
      nombre: "",
      email: "",
      password: "",
      error: false,
      loading : false
     
    };
  },

  methods: {
    register() {
      
     this.error=false
     this.loading= false
    

      axios.post("http://localhost:1337/auth/local/register/",
   
      {
         
        username: this.username,
        nombre: this.nombre,
        email: this.email,
        password: this.password,

        headers: {
          "Content-Type": "application/json",
        },
      })
       .then((response) => {
                this.loading= true
               // this.$router.push('/login')
            })
      
     .catch((err) =>{
       console.log('Fallo')
       this.error=true
     });
     

    },
  },
};
</script>
<style>
</style>