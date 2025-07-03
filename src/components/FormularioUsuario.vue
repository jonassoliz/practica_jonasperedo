<script setup>
import { ref } from 'vue';
import EntradaDatos from './EntradaDatos.vue';

const nombre = ref('');
const correo = ref('');
const telefono = ref('');
const error = ref('');
const emit = defineEmits(['nuevoUsuario']);

// Validaciones
const regexCorreo = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
const regexTelefono = /^[0-9]{8}$/;

const enviarFormulario = () => {
  if (!nombre.value || !correo.value || !telefono.value) {
    error.value = 'Todos los campos son obligatorios';
    return;
  }

  if (!regexCorreo.test(correo.value)) {
    error.value = 'El correo no tiene un formato válido';
    return;
  }

  if (!regexTelefono.test(telefono.value)) {
    error.value = 'El teléfono debe tener exactamente 8 dígitos numéricos (Bolivia)';
    return;
  }

  // Emitir evento con los datos
  emit('nuevoUsuario', {
    nombre: nombre.value,
    correo: correo.value,
    telefono: telefono.value,
  });

  // Mostrar mensaje de éxito
  alert('Registro exitoso');

  // Limpiar campos
  nombre.value = '';
  correo.value = '';
  telefono.value = '';
  error.value = '';
};
</script>



<template>
  <form @submit.prevent="enviarFormulario">
    <EntradaDatos label="Nombre" v-model="nombre" type="text" placeholder="Ingrese su nombre" />
    <EntradaDatos label="Correo" v-model="correo" type="email" placeholder="Ingrese su correo electro" />
    <EntradaDatos label="Teléfono" v-model="telefono" type="text" placeholder="Ingrese su numero telefonico" />
    <p v-if="error" class="error">{{ error }}</p>
    <button type="submit">Guardar</button>
  </form>
</template>
