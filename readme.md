[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/MdNm2wHB)
# 🧩 Trabajo Práctico N°2 : Gestión de Productos (Vuejs) 
## Capa Vista

## 🎯 Objetivo

Desarrollar una aplicación en Vue 3 que permita simular la gestión de productos desde la capa de presentación, emulando una interacción con una capa de negocios (sin backend real). para este trabajo práctico de deberá crear una aplicacion en VUEjs como hemos visto en clases pasadas.

Se deberán aplicar los siguientes conceptos:

- `ref` y `reactive`
- `v-model`
- Directivas (`v-if`, `v-for`, `v-on`)
- Propiedades computadas (`computed`)
- Comunicación entre componentes (`props` y `emits`)

---

## 📋 Consigna

Desarrollar una aplicación que permita:

### 1. Crear productos

Implementar un formulario con los siguientes campos:

- Nombre del producto
- Precio
- Stock
- Categoría (select)

Requisitos:
- Validar que los campos no estén vacíos
- El precio y el stock deben ser valores numéricos válidos

📌 Conceptos:
- `ref`
- `v-model`
- Eventos (`@submit`, `@click`)

---

### 2. Guardar productos

Los productos deben almacenarse en un **array en memoria** (estado local en Vue).

Cada producto debe tener la siguiente estructura:

```json
{
  "id": Number,
  "nombre": String,
  "precio": Number,
  "stock": Number,
  "categoria": String
}
```

📌 Importante:
- El `id` debe generarse automáticamente
- Simular que se está enviando a una capa de negocio (por ejemplo, usando funciones separadas o comentarios claros)

---

### 3. Listar productos

Mostrar todos los productos en una lista o tabla.

📌 Conceptos:
- `reactive`
- `v-for`
- `:key` obligatorio

---

### 4. Eliminar producto

Cada producto debe tener un botón para eliminarlo.

📌 Conceptos:
- `emits`
- Manejo de eventos desde componentes hijos

---
### 5. Filtrar productos

Agregar un filtro que permita:

- Mostrar todos
- Filtrar por categoría

📌 Conceptos:
- `computed`

---

### 6. Resumen de productos

Mostrar:

- Cantidad total de productos
- Valor total del inventario (precio * stock)

📌 Conceptos:
- `computed`

---

## 🧱 Estructura obligatoria

Separar la aplicación en componentes:

- `App.vue` → Manejo del estado global
- `ProductForm.vue` → Formulario de carga
- `ProductList.vue` → Lista de productos
- `ProductItem.vue` → Producto individual

📌 Requisitos:
- Uso obligatorio de `props`
- Uso obligatorio de `emits`
- No mutar props directamente

---

## ⚙️ Requisitos técnicos

- Usar **Composition API (`<script setup>`)**
- No utilizar librerías externas
- Mantener el estado en `App.vue`
- Código claro y organizado

---

## 🧠 Simulación de capa de negocios

Aunque no hay backend, se debe:

- Separar la lógica de creación/eliminación en funciones
- Simular una "llamada" a la capa de negocio (por ejemplo):
  - Función `crearProducto(producto)`
  - Función `eliminarProducto(id)`

Esto puede implementarse como funciones dentro del mismo componente o en un archivo separado.

---

## Errores a evitar

- Mutar `props` directamente
- No usar `key` en `v-for`
- Mezclar toda la lógica en un solo componente
- No validar los datos del formulario
- No separar responsabilidades

---

## 🕒 Fecha de entrega

8/05/2026

---
