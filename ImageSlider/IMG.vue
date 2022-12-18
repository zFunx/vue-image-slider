<template>
  <img class="img" :src="src" :width="width" :height="height" />
</template>
<script setup>
import { defineProps } from "vue";

defineProps({
  src: {
    type: String,
    required: true,
  },
  height: {
    type: Number,
    default: 300,
  },
  width: {
    type: Number,
    default: 300,
  },
});
</script>
<style scoped>
.img {
  position: absolute;
  object-fit: cover;
  object-position: center;
}
</style>