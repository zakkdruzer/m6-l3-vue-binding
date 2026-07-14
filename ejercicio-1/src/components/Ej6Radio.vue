<script setup>
import { ref } from 'vue'

const calificacion = ref('')
</script>

<template>
  <div class="ej-radio">
    <h3>¿Cómo calificarías la clase?</h3>

    <label>
      <input
        type="radio"
        value="Excelente"
        v-model="calificacion"
      />
      Excelente
    </label>

    <label>
      <input
        type="radio"
        value="Buena"
        v-model="calificacion"
      />
      Buena
    </label>

    <label>
      <input
        type="radio"
        value="Regular"
        v-model="calificacion"
      />
      Regular
    </label>

    <label>
      <input
        type="radio"
        value="Mala"
        v-model="calificacion"
      />
      Mala
    </label>

    <p>Opción elegida: {{ calificacion || 'ninguna' }}</p>

    <p v-if="calificacion === 'Excelente' || calificacion === 'Buena'">
      ¡Gracias por tu buena evaluación!
    </p>
    <p v-else-if="calificacion === 'Regular'">
      Gracias por tu sinceridad, veremos cómo mejorar.
    </p>
    <p v-else-if="calificacion === 'Mala'">
      Sentimos que tu experiencia no fue buena, cuéntanos más.
    </p>
  </div>
</template>