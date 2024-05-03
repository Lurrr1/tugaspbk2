<template>
  <div>
    <h1 :style="titleStyles">Hello, {{ name }}</h1>
    <input
      type="text"
      v-model="name"
      @input="handleInput"
      :class="{ 'input-error': isError }"
    />
    <p v-if="isError" class="error-message">Name cannot be empty!</p>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";

const name = ref("");
const isError = ref(false);

const titleStyles = computed(() => ({
  color: isError.value ? "red" : "black",
}));

const handleInput = () => {
  if (name.value === "") {
    isError.value = true;
  } else {
    isError.value = false;
  }
};
</script>

<style scoped>
h1 {
  font-family: Arial, sans-serif;
}

.input-error {
  border: 1px solid red;
}

.error-message {
  color: red;
}
</style>
