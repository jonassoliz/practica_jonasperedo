<!-- src/App.vue -->
<script setup>
import { ref } from 'vue';
import FormularioUsuario from './components/FormularioUsuario.vue';
import ListaUsuarios from './components/ListaUsuarios.vue';

const usuarios = ref([]);

function eliminarUsuario(index) {
  usuarios.value.splice(index, 1);
}

const agregarUsuario = (usuario) => {
  usuarios.value.push(usuario);
};
</script>

<template>
  <!-- SIDEBAR MODERNO -->
  <div class="sidebar">
    <div class="sidebar-logo">Mi App</div>
    <ul class="sidebar-links">
      <li><a href="#" class="active"><i class="fas fa-home"></i> Inicio</a></li>
      <li><a href="#"><i class="fas fa-user-plus"></i> Registro</a></li>
      <li><a href="#"><i class="fas fa-users"></i> Usuarios</a></li>
      <li><a href="#"><i class="fas fa-cog"></i> Configuración</a></li>
    </ul>
  </div>

  <!-- CONTENIDO PRINCIPAL -->
  <div class="contenedor">
    <h1>Registro de Usuarios</h1>
    <FormularioUsuario @nuevoUsuario="agregarUsuario" />
    <ListaUsuarios :usuarios="usuarios" @eliminar="eliminarUsuario" />
  </div>
</template>
