<script setup>

import { ref } from 'vue'

defineProps({
  categorias: {
    type: Array,
    required: true
  }
})

const emit = defineEmits(['guardar-producto'])

const nombre = ref('')
const precio = ref('')
const stock = ref('')
const categoria = ref('')
const mensajeError = ref('')

function limpiarCampos() {
  nombre.value = ''
  precio.value = ''
  stock.value = ''
  categoria.value = ''
}

function validarYGuardar() {
  mensajeError.value = ''

  if (!nombre.value.trim() || !precio.value || !stock.value || !categoria.value) {
    mensajeError.value = 'Debés completar todos los datos del producto.'
    return
  }

  const precioFinal = Number(precio.value)
  const stockFinal = Number(stock.value)

  if (isNaN(precioFinal) || precioFinal <= 0) {
    mensajeError.value = 'El precio debe ser un número mayor a cero.'
    return
  }

  if (isNaN(stockFinal) || stockFinal < 0) {
    mensajeError.value = 'El stock debe ser un número válido.'
    return
  }

  emit('guardar-producto', {
    nombre: nombre.value.trim(),
    precio: precioFinal,
    stock: stockFinal,
    categoria: categoria.value
  })

  limpiarCampos()
}
</script>

<template>
  <form class="formulario" @submit.prevent="validarYGuardar">
    <h2>Nuevo Producto</h2>

    <input
      v-model="nombre"
      type="text"
      placeholder="Nombre del producto"
    />

    <input
      v-model="precio"
      type="number"
      placeholder="Precio"
    />

    <input
      v-model="stock"
      type="number"
      placeholder="Stock"
    />

    <select v-model="categoria">
      <option value="" disabled>Elegir categoría</option>
      <option
        v-for="item in categorias"
        :key="item"
        :value="item"
      >
        {{ item }}
      </option>
    </select>

    <p v-if="mensajeError" class="error">
      {{ mensajeError }}
    </p>

    <button type="submit">Agregar Producto</button>
  </form>
</template>