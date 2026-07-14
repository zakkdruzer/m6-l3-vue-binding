<script setup>
import { ref } from 'vue'

const estado = ref('verde')
</script>

<template>
  <div class="contenedor-semaforo">
    <div
      class="circulo"
      :style="{
        background: estado === 'verde'
          ? 'green'
          : estado === 'amarillo'
            ? 'yellow'
            : 'red'
      }"
    ></div>

    <div class="botones">
      <button @click="estado = 'verde'">Verde</button>
      <button @click="estado = 'amarillo'">Amarillo</button>
      <button @click="estado = 'rojo'">Rojo</button>
    </div>

    <p>Estado actual: {{ estado }}</p>
  </div>
</template>

<style scoped>
.contenedor-semaforo {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
  margin: 2rem 0;
}

.circulo {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  border: 2px solid #333;
}

.botones button {
  margin: 0 0.25rem;
}
</style>