<script setup>
    import {ref} from 'vue'
    import {onMounted, computed} from 'vue'
    import { datos } from '../datos.js'

    const i = ref(0)
    const total = datos.length
    const img = ref('')
    const nombre = ref('')
    const precio = ref()
    const finDeSemana = ref()
    const dcto = ref(false)
    
    const render = onMounted(()=>{
      primeraLetraMayus(datos[i.value].nombre) 
      img.value = 'https://www.html6.es/img/rey_'+datos[i.value].nombre+'.png'
      precio.value = datos[i.value].precio
      if(precio.value<100){dcto.value = true}else{dcto.value = false}
      finDeSemana.value = datos[i.value].finDeSemana
    })

    const primeraLetraMayus = (str) =>{
      let lowCase = str.toLowerCase().slice(1)
      let subStr = str.substring(0,1).toUpperCase()
      return nombre.value = subStr+lowCase
    }

    const siguiente = ()=>{
      i.value++
      if(i.value>=total){ i.value = 0 
        } render()
    }

    
</script>

<template>

  <div class="card text-center">
      <h5 class="card-title d-inline-block">Cena {{ i+1 }} con el rey 
      <h5 class="d-inline-block descuento">{{ nombre }}</h5></h5>
      <div class="card-body">
          <h5 class="card-text d-inline-block">Precio: 
            <h5 class="card-text d-inline-block" :class="precio < 100 ? 'descuento' : '' ">{{ precio }}Є</h5>
          </h5>
          <div class="card-text">
            <span v-if="finDeSemana" class="my-2 d-inline-block btn-sm btn-danger">Solo fines de semana</span>
            <span v-if="!finDeSemana" class="my-2 d-inline-block btn-sm btn-success">De lunes a domingo</span>
          </div>
          <div v-show="dcto" >
          <p class="d-inline-block ">Ahora con 10% de dcto:  {{ precio*0.9 }}</p>
          <img  src="oferta.jpg" class="img-fluid align-middle w-25 d-inline-block">
          </div>
          <img  :src="img" class="card-img-top" alt="Descripción de la imagen principal">
          <button class="btn btn-primary btn-block mt-3" @click="siguiente" >Siguiente {{ i+1}} / {{ total }}</button>
      </div>
    </div>

</template>

<style scoped>
  .descuento{
    color: green;
  }
</style>