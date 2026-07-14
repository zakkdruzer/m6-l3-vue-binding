<script setup>
import { ref } from 'vue'

const nota = ref('')
</script>

<template>
  <div class="ej-textarea">
    <label>
      Escribe tu nota:
      <textarea
        v-model="nota"
        rows="5"
        cols="40"
      ></textarea>
    </label>

    <p
      :style="{
        color: nota.length > 200 ? 'red' : 'black'
      }"
    >
      Caracteres: {{ nota.length }}
    </p>

    <h3>Vista previa</h3>
    <pre>{{ nota }}</pre>
  </div>
</template>