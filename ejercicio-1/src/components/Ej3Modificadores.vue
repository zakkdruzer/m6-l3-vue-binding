<script setup>
import { ref } from 'vue'

const a = ref('')
const b = ref('')

const aNumero = ref('')
const bNumero = ref('')

const usuario = ref('')
const email = ref('')
</script>

<template>
  <div class="ej-modificadores">
    <section>
      <h3>Suma sin .number</h3>
      <input type="" v-model="a" placeholder="a" />
      <input type="" v-model="b" placeholder="b" />
      <p>a + b = {{a + b}} (tipo a: {{ typeof a }}, tipo b: {{ typeof b }})</p>
    </section>

    <section>
      <h3>Suma con .number</h3>
      <input type="number" v-model.number="aNumero" placeholder="aNumero" />
      <input type="number" v-model.number="bNumero" placeholder="bNumero" />
      <p>
        aNumero + bNumero = {{ aNumero + bNumero }}
        (tipo aNumero: {{ typeof aNumero }}, tipo bNumero: {{ typeof bNumero }})
      </p>
    </section>

    <section>
      <h3>Usuario con .trim</h3>
      <input type="text" v-model.trim="usuario" placeholder="usuario" />
      <p>Valor: '{{ usuario }}' (largo: {{ usuario.length }})</p>
    </section>

    <section>
      <h3>Email con .lazy</h3>
      <input type="email" v-model.lazy="email" placeholder="email" />
      <p>Email guardado: {{ email }}</p>
    </section>
  </div>
</template>