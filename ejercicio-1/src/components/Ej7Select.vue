<script setup>
import { ref } from 'vue'

const plan = ref('')

const precios = {
  basico: 0,
  pro: 9990,
  premium: 19990,
}
</script>

<template>
  <div class="ej-select">
    <h3>Elige tu plan</h3>

    <select v-model="plan">
      <option disabled value="">Selecciona un plan</option>
      <option value="basico">Básico</option>
      <option value="pro">Pro</option>
      <option value="premium">Premium</option>
    </select>

    <p v-if="plan">
      Plan elegido: {{ plan }} —
      Precio:
      {{
        precios[plan].toLocaleString('es-CL', {
          style: 'currency',
          currency: 'CLP',
        })
      }}
    </p>
    <p v-else>
      Aún no has elegido un plan.
    </p>

    <button :disabled="!plan">
      Contratar
    </button>
  </div>
</template>