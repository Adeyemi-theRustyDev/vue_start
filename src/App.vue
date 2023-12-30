<script setup>
  import { ref } from 'vue'

  const inputVal = ref('Initial value');

  const changeValue = e => inputVal.value = e.target.value
</script>
<template>
  <h1>{{ inputVal }}</h1>
  <input type="text" :value="inputVal" @input="changeValue">
</template>
<style scoped>
</style>