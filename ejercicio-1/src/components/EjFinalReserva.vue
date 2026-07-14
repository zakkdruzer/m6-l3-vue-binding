<script setup>
import { ref, computed } from 'vue'

const nombre = ref('')
const noches = ref(1)

const habitacion = ref('') // 'individual' | 'doble' | 'suite'
const regimen = ref('')    // 'solo', 'desayuno', 'pension'

const extrasSeleccionados = ref([])

const fumador = ref('no-fumador')

const peticiones = ref('')

const aceptaPolitica = ref(false)

// precios habitación por noche
const preciosHabitacion = {
  individual: 30000,
  doble: 50000,
  suite: 80000,
}

// extras con precio
const extrasDefinicion = [
  { id: 'wifi', nombre: 'WiFi premium', precio: 5000 },
  { id: 'estacionamiento', nombre: 'Estacionamiento', precio: 8000 },
  { id: 'spa', nombre: 'Spa', precio: 15000 },
]

// utilidad: obtener precio de extras seleccionados
const totalExtras = computed(() => {
  return extrasSeleccionados.value.reduce((suma, idExtra) => {
    const extra = extrasDefinicion.find(e => e.id === idExtra)
    return suma + (extra ? extra.precio : 0)
  }, 0)
})

// precio total
const total = computed(() => {
  const nochesNumero = Number(noches.value) || 0

  const precioHab = habitacion.value
    ? preciosHabitacion[habitacion.value]
    : 0

  return precioHab * nochesNumero + totalExtras.value
})

// botón Reservar deshabilitado si falta algo
const botonDeshabilitado = computed(() => {
  return !nombre.value.trim() || !habitacion.value || !aceptaPolitica.value
})
</script>

<template>
  <div class="reserva">
    <h2>Reserva de hotel</h2>

    <!-- Nombre -->
    <label>
      Nombre del huésped:
      <input
        type="text"
        v-model.trim="nombre"
      />
    </label>

    <!-- Noches -->
    <label>
      Cantidad de noches:
      <input
        type="number"
        min="1"
        v-model.number="noches"
      />
    </label>

    <!-- Habitación -->
    <label>
      Tipo de habitación:
      <select v-model="habitacion">
        <option disabled value="">Selecciona una habitación</option>
        <option value="individual">Individual</option>
        <option value="doble">Doble</option>
        <option value="suite">Suite</option>
      </select>
    </label>

    <!-- Régimen -->
    <fieldset>
      <legend>Régimen</legend>

      <label>
        <input
          type="radio"
          value="solo"
          v-model="regimen"
        />
        Solo alojamiento
      </label>

      <label>
        <input
          type="radio"
          value="desayuno"
          v-model="regimen"
        />
        Desayuno incluido
      </label>

      <label>
        <input
          type="radio"
          value="pension"
          v-model="regimen"
        />
        Pensión completa
      </label>
    </fieldset>

    <!-- Extras -->
    <fieldset>
      <legend>Servicios extra</legend>

      <label v-for="extra in extrasDefinicion" :key="extra.id">
        <input
          type="checkbox"
          :value="extra.id"
          v-model="extrasSeleccionados"
        />
        {{ extra.nombre }} ({{ extra.precio.toLocaleString('es-CL') }})
      </label>
    </fieldset>

    <!-- Fumador -->
    <label>
      <input
        type="checkbox"
        v-model="fumador"
        :true-value="'fumador'"
        :false-value="'no-fumador'"
      />
      ¿Fumador?
    </label>

    <!-- Peticiones especiales -->
    <label>
      Peticiones especiales:
      <textarea v-model="peticiones"></textarea>
    </label>

    <!-- Política -->
    <label>
      <input
        type="checkbox"
        v-model="aceptaPolitica"
      />
      Acepto la política de cancelación
    </label>

    <!-- Resumen -->
    <section class="resumen">
      <h3>Resumen de la reserva</h3>
      <p>Nombre: {{ nombre || '—' }}</p>
      <p>Noches: {{ noches }}</p>
      <p>Habitación: {{ habitacion || '—' }}</p>
      <p>Régimen: {{ regimen || '—' }}</p>
      <p>Extras: {{ extrasSeleccionados.join(', ') || 'Ninguno' }}</p>
      <p>Fumador: {{ fumador }}</p>
      <p>Peticiones: {{ peticiones || 'Ninguna' }}</p>
      <p>
        Total:
        {{
          total.toLocaleString('es-CL', {
            style: 'currency',
            currency: 'CLP',
          })
        }}
      </p>
    </section>

    <button :disabled="botonDeshabilitado">
      Reservar
    </button>
  </div>
</template>