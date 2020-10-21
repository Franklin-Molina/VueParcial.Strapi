<template>
  <div>
    <h1>Registro</h1>
     <form @submit.prevent="register">

    
    <label for="username">Nombre</label> <strong style="color:red"> * </strong>
    <input type="text" v-model="username" required>  <br> 

    <label for="apellido" >Apellido </label> <strong style="color:red"> * </strong>
    <input type="text" v-model="apellido" required><br>
    <label for="email" >Email </label> <strong style="color:red"> * </strong>
    <input type="email" v-model="email" required><br>
    <label for="password">Password </label> <strong style="color:red"> * </strong>
    <input type="password" v-model="password" required><br>

    <button type="submit">Registrar</button>


    </form>
  

  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Registro',
  data() {
    return {
      username: '',
      apellido: '',
      email: '',
      password: '',

    }
  },

  methods: {
    register(){
     axios.post("http://localhost:1337/auth/local/register/",{

       username: this.username,
       apellido: this.apellido,
       email: this.email,
       password: this.password,
       
       headers:{
         'Content-Type':'application/json'
       },
       

       

     })
    }
  }

  
}
</script>
<style>
   
</style>