<template>
  <input
    class="input"
    :class="{ inputOngoing, inputError }"
    type="text"
    @focus="focus = true"
    @blur="focus = true"
    v-model="input"
  />
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';

const input = ref('');
const focus = ref('');

const inputOngoing = computed(() => focus.value && input.value.length);
const inputError = computed(() => input.value.length < 5);
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
.inputError {
  border-color: red;
}
</style>
