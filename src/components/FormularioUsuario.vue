<!-- src/components/Formulario.vue -->
<script setup>
import { ref } from 'vue';
import EntradaDatos from './EntradaDatos.vue';

const nombre = ref('');
const correo = ref('');
const telefono = ref('');
const error = ref('');
const emit = defineEmits(['nuevoUsuario']);

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

  emit('nuevoUsuario', {
    nombre: nombre.value,
    correo: correo.value,
    telefono: telefono.value,
  });

  alert('Registro exitoso');

  nombre.value = '';
  correo.value = '';
  telefono.value = '';
  error.value = '';
};
</script>

<template>
  <form @submit.prevent="enviarFormulario" class="formulario-card">
    <EntradaDatos label="Nombre" v-model="nombre" type="text" placeholder="Ingrese su nombre" />
    <EntradaDatos label="Correo" v-model="correo" type="email" placeholder="Ingrese su correo electrónico" />
    <EntradaDatos label="Teléfono" v-model="telefono" type="text" placeholder="Ingrese su número telefónico" />
    <p v-if="error" class="error">{{ error }}</p>
    <button type="submit">
      <i class="fas fa-save"></i> Guardar
    </button>
  </form>
</template>
