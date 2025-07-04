<!-- src/components/EntradaDatos.vue -->
<script setup>
const props = defineProps(['label', 'type', 'placeholder', 'modelValue']);
const emit = defineEmits(['update:modelValue']);
</script>

<template>
  <div class="entrada-datos">
    <label>{{ label }}</label>
    <input
      :type="type"
      :placeholder="placeholder"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
    />
  </div>
</template>
