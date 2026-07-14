<script setup>
import { ref } from 'vue'

const suscrito = ref(false)

const hobbies = ref([])

const modo = ref('gratis')
</script>

<template>
  <div class="ej-checkbox">
    <section>
      <h3>Suscripción (booleano)</h3>
      <label>
        <input type="checkbox" v-model="suscrito" />
        Suscribirme al newsletter
      </label>
      <p>Suscrito: {{ suscrito }}</p>
    </section>
    <section>
      <h3>Hobbies (array)</h3>

      <label>
        <input
          type="checkbox"
          value="leer"
          v-model="hobbies"
        />
        Leer
      </label>

      <label>
        <input
          type="checkbox"
          value="deporte"
          v-model="hobbies"
        />
        Deporte
      </label>

      <label>
        <input
          type="checkbox"
          value="musica"
          v-model="hobbies"
        />
        Música
      </label>

      <p>Hobbies seleccionados: {{ hobbies }}</p>
      <p>Cantidad: {{ hobbies.length }}</p>
    </section>
    <section>
      <h3>Modo con valores personalizados</h3>
      <label>
        <input
          type="checkbox"
          v-model="modo"
          :true-value="'pro'"
          :false-value="'gratis'"
        />
        Modo PRO
      </label>
      <p>Modo actual: {{ modo }}</p>
    </section>
  </div>
</template>