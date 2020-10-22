
<template>

 
   
    
      <div class="imgBx">
        <img id="imagenes" :src="items.url.url" class="card-img-top" />
      </div>
      
      <div class="details">
     
    
      <h5 class="card-title">{{ items.user.username}}</h5>
        
      
      </div>

``

  
</template>

<script>
export default {
  name: "Imagen",
  props: ["items"],
};
</script>