<template>
  <input
    class="input"
    :class="{ inputOngoing, inputError, inputValid }"
    type="text"
    @focus="
      focus = true;
      touched = true;
    "
    @blur="focus = true"
    v-model="input"
  />
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';

const input = ref('');
const focus = ref(false);
const touched = ref(false);

const inputOngoing = computed(() => focus.value && input.value.length);
const inputError = computed(
  () => !focus.value && touched.value && input.value.length < 5
);
const inputValid = computed(
  () => !focus.value && touched.value && !inputError.value
);
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
.inputValid {
  border-color: green;
}
</style>
