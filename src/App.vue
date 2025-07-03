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
  <div class="layout">
    <aside class="sidebar">
      <div class="sidebar-logo">Mi Empresa</div>
      <ul class="sidebar-links">
        <li><a href="#">Inicio</a></li>
        <li><a href="#">Clientes</a></li>
        <li><a href="#">Contacto</a></li>
      </ul>
    </aside>
  </div>
  <h1>Registro de Usuarios</h1>
  <FormularioUsuario @nuevoUsuario="agregarUsuario" />
  <ListaUsuarios :usuarios="usuarios" @eliminar="eliminarUsuario" />
  
</template>
