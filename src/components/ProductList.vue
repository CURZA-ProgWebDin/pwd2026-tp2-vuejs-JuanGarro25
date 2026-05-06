<script setup>

import ProductItem from './ProductItem.vue'

defineProps({
  productos: {
    type: Array,
    required: true
  }
})

const emit = defineEmits(['borrar-producto'])

function enviarIdProducto(id) {
  emit('borrar-producto', id)
}
</script>

<template>
  <section class="listado">
    
    <p v-if="productos.length === 0" class="sin-productos">
      Todavía no hay productos cargados.
    </p>

    <div v-else class="grilla-productos">
      <ProductItem
        v-for="producto in productos"
        :key="producto.id"
        :producto="producto"
        @borrar-producto="enviarIdProducto"
      />
    </div>
  </section>
</template>