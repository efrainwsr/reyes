<script setup>
    import {ref} from 'vue'
    import {onMounted} from 'vue'
    import { datos } from '../datos.js'

    const contador = ref(0)
    const total = datos.length
    const img = ref()
    
    const siguiente = ()=>{
        contador.value++
        if(contador.value>=total){
            contador.value = 0
        }
    }

    img.value = 'https://www.html6.es/img/rey_'+datos[contador.value].nombre+'.png'


</script>

<template>
 <div class="card text-center">
    <h5 class="card-title">Cena {{ contador+1 }} con el rey {{ }}</h5>
     <div class="card-body ">
        <p class="card-text">{{  }}</p>
        <p class="card-text">
          {{  }}
          <img src="/oferta.jpg" class="img-fluid align-middle w-25" alt="Descripción de la imagen pequeña">
          {{  }}
        </p>
        <img  :src="img" class="card-img-top" alt="Descripción de la imagen principal">
        <button class="btn btn-primary btn-block mt-3" @click="siguiente" >Siguiente {{ contador+1}} / {{ total }}</button>
     </div>
   </div>
</template>