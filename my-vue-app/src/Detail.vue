<template>
  <div class="mt-300">
    asd
    <h1>Product ID: {{ id }}</h1>
  </div>
</template>

<script setup>
import { useRoute } from 'vue-router'
const route = useRoute();
const id = route.params.id;
</script>
