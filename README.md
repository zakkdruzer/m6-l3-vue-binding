# Formularios con Vue 3 + Vite

Proyecto de práctica para trabajar formularios en **Vue 3** usando **Composition API** con `<script setup>` y Vite.  
Incluye ejercicios de `v-bind`, `v-model`, modificadores, textarea, checkbox, radio, select y un formulario final de reserva de hotel.

## Ejercicios incluidos

Cada ejercicio vive en su propio componente dentro de `src/components`:

- `Ej1Semaforo.vue` — Binding unidireccional con `v-bind` / `:style`
- `Ej2Saludo.vue` — `v-model` básico en `<input>`
- `Ej3Modificadores.vue` — Modificadores `.trim`, `.number`, `.lazy`
- `Ej4Textarea.vue` — `v-model` en `<textarea>` y contador de caracteres
- `Ej5Checkbox.vue` — Checkbox en modo booleano, array y valores personalizados
- `Ej6Radio.vue` — Radio buttons con un solo `v-model`
- `Ej7Select.vue` — Select con placeholder, precio y botón deshabilitado
- `EjFinalReserva.vue` — Formulario completo de reserva de hotel con `computed` para el total

En `App.vue` se importan y muestran estos componentes (uno debajo del otro o con algún selector simple).

## Tech stack

- [Vue 3](https://vuejs.org/) con Composition API (`<script setup>`)
- [Vite](https://vite.dev/) como bundler
- JavaScript (ESM)
- CSS simple (global y `scoped` en algunos componentes)

## Estructura del proyecto

```txt
src/
├── App.vue
├── main.js
├── style.css
└── components/
    ├── Ej1Semaforo.vue
    ├── Ej2Saludo.vue
    ├── Ej3Modificadores.vue
    ├── Ej4Textarea.vue
    ├── Ej5Checkbox.vue
    ├── Ej6Radio.vue
    ├── Ej7Select.vue
    └── EjFinalReserva.vue
```

## Scripts disponibles

```bash
# instalar dependencias
npm install

# entorno de desarrollo
npm run dev

# build de producción
npm run build

# vista previa del build
npm run preview

# desplegar a GitHub Pages (usa gh-pages y /dist)
npm run deploy
```

> Nota: el script `deploy` asume que el proyecto está configurado con `gh-pages` y que el `base` de Vite coincide con el nombre del repositorio.

## Configuración para GitHub Pages

En `vite.config.[js|ts]` se configura el `base` para que coincida con el nombre del repositorio:

```js
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'

export default defineConfig({
  plugins: [vue()],
  base: '/nombre-del-repo/', // reemplazar por el nombre real
})
```

En `package.json` se añaden los scripts de despliegue:

```json
{
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview",
    "predeploy": "npm run build",
    "deploy": "gh-pages -d dist"
  }
}
```

Después de ejecutar:

```bash
npm run deploy
```

se puede activar GitHub Pages desde la rama `gh-pages` en **Settings → Pages**.

## Objetivos de aprendizaje

- Entender la diferencia entre `v-bind` y `v-model`
- Practicar los modificadores `.trim`, `.number`, `.lazy` en `v-model`
- Usar inputs de texto, número, textarea, checkbox, radio y select
- Calcular valores derivados con `computed` (precio total de la reserva)
- Deshabilitar elementos con `:disabled` según condiciones del estado
- Preparar y publicar una app Vite + Vue en GitHub Pages

## Puedes ver el resultado en:

https://zakkdruzer.github.io/m6-l3-vue-binding/
