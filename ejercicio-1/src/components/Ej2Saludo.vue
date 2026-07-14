<script setup>
import { ref } from 'vue'

const nombre = ref('')
</script>

<template>
  <div class="ej-saludo">
    <label>
      Escribe tu nombre:
      <input type="text" v-model="nombre" />
    </label>

    <h2>¡Hola, {{ nombre || 'visitante' }}!</h2>
  </div>
</template>