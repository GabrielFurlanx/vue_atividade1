<template>
  <p> {{ valor }}</p>
  <button style="display: block" @click="incrementar"> Incrementar </button>
</template>

<script setup>
import { ref, onBeforeMount, onMounted, onBeforeUpdate, onUpdated } from 'vue'

  const valor = ref(0)

  function incrementar() {
    valor.value++
  }

  onBeforeMount(() => {
    console.log('Antes de montar')
  })

  onMounted(() => {
    console.log('Componente Montado')
  })

  onBeforeUpdate(() => {
    console.log('Antes de atualizar')
  })

  onUpdated(() => {
    console.log('Depois de Atualizar')
  })

</script>
