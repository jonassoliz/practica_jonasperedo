<!-- src/components/EntradaDatos.vue -->
<script setup>
import { ref, watch } from 'vue';

const props = defineProps(['label', 'type', 'placeholder', 'modelValue']);
const emit = defineEmits(['update:modelValue']);
const inputValue = ref(props.modelValue);

watch(() => props.modelValue, (nuevo) => {
  inputValue.value = nuevo;
});
</script>

<template>
  <div>
    <label>{{ label }}</label>
    <input
      :type="type"
      :placeholder="placeholder"
      v-model="inputValue"
      @input="$emit('update:modelValue', inputValue)"
    />
  </div>
</template>
