<template>
  <div class="py-5">
    <h4>Sua carteira:</h4>
    <h1>R${{ total }}</h1>
  </div>
</template>

<script setup>
import { defineProps } from "vue";
const props = defineProps({
  total: Number,
});
</script>
