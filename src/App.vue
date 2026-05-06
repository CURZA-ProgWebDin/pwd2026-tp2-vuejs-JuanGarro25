<script setup>

import { computed, reactive, ref } from 'vue'
import ProductForm from './components/ProductForm.vue'
import ProductList from './components/ProductList.vue'

const categorias = ['Electrónica', 'Indumentaria', 'Almacén', 'Herramientas']

const productos = reactive([])
const categoriaSeleccionada = ref('Todas')
let siguienteId = 1

function guardarProducto(nuevoProducto) {
  productos.push({
    id: siguienteId++,
    ...nuevoProducto
  })
}

function borrarProducto(id) {
  const posicion = productos.findIndex((producto) => producto.id === id)

  if (posicion !== -1) {
    productos.splice(posicion, 1)
  }
}

const productosFiltrados = computed(() => {
  if (categoriaSeleccionada.value === 'Todas') {
    return productos
  }

  return productos.filter(
    (producto) => producto.categoria === categoriaSeleccionada.value
  )
})

const totalProductos = computed(() => productos.length)

const totalInventario = computed(() => {
  return productos.reduce(
    (total, producto) => total + producto.precio * producto.stock,
    0
  )
})
</script>

<template>
  <main class="contenedor">
    <h1 class="titulo-principal">Gestión de Productos</h1>

    <ProductForm
      :categorias="categorias"
      @guardar-producto="guardarProducto"
    />

    <section class="resumen">
      <h2>Resumen del Inventario</h2>
      <p>Total de Productos: {{ totalProductos }}</p>
      <p>Valor Total: ${{ totalInventario }}</p>
    </section>
    <h2>Listado de Productos</h2>
    <section class="filtro">
      <label>Filtrar por Categoría:</label>

      <select v-model="categoriaSeleccionada">
        <option>Todas</option>
        <option
          v-for="categoria in categorias"
          :key="categoria"
        >
          {{ categoria }}
        </option>
      </select>
    </section>

    <ProductList
      :productos="productosFiltrados"
      @borrar-producto="borrarProducto"
    />
  </main>
</template>