<script setup>
import { ArrowUpRight } from "lucide-vue-next";
</script>
<script>

export default {
  props: {
    text: String,
    
  }
}

</script>
<template>
  <div>
    <a
      style="background-image: linear-gradient(to right, #2d2fe1, #732eb5)"
      href="#"
      class="inline-flex items-center justify-center px-5 py-3 text-base font-medium text-center text-white bg-blue-700 rounded-lg focus:ring-4 focus:ring-blue-300"
    >
      {{text}}

      <ArrowUpRight />
    </a>
  </div>
</template>
