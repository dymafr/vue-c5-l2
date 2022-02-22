<template>
  <input
    class="input"
    :class="{ inputOngoing: inputOngoing }"
    type="text"
    v-model="input"
  />
</template>

<script setup lang="ts">
import { ref } from 'vue';

const input = ref('');
const inputOngoing = computed(() => input.value.length);
</script>

<style scoped>
input {
  outline: 0;
  border: 2px solid black;
  border-radius: 4px;
}
.inputOngoing {
  border-color: blue;
}
</style>
