<script setup>

const props = defineProps({
  producto: {
    type: Object,
    required: true
  }
})

const emit = defineEmits(['borrar-producto'])

function borrar() {
  emit('borrar-producto', props.producto.id)
}
</script>

<template>
  <article class="tarjeta-producto">
    <h3>{{ producto.nombre }}</h3>

    <p>Categoría: {{ producto.categoria }}</p>
    <p>Precio: ${{ producto.precio }}</p>
    <p>Stock disponible: {{ producto.stock }}</p>
    <p>Subtotal: ${{ producto.precio * producto.stock }}</p>

    <button type="button" @click="borrar">
      Quitar producto
    </button>
  </article>
</template>