<!-- src/components/ListaUsuarios.vue -->
<script setup>
const props = defineProps(['usuarios']);
const emit = defineEmits(['eliminar']);

function eliminarUsuario(index) {
  emit('eliminar', index);
  alert('Usuario eliminado correctamente');
}
</script>

<template>
  <h1>Lista de usuarios</h1>
  <div class="tabla-usuarios-wrapper">
    <table class="tabla-usuarios">
      <thead>
        <tr>
          <th>Nombre</th>
          <th>Correo</th>
          <th>Teléfono</th>
          <th>Acción</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(usuario, i) in usuarios" :key="i">
          <td>{{ usuario.nombre }}</td>
          <td>{{ usuario.correo }}</td>
          <td>{{ usuario.telefono }}</td>
          <td>
            <button @click="eliminarUsuario(i)">
              <i class="fas fa-trash-alt"></i> Eliminar
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
