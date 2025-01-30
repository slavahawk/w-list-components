<template>
<div v-if="pricePerGlass" class="flex gap-2 items-center">
  <Glass />
  <span>{{ formatPrice(pricePerGlass) }}</span>
  <sub v-if="glassVolume" class="text-xs items-end">{{ glassVolume }} мл</sub>
</div>
</template>

<script setup lang="ts">
import { formatPrice } from "w-list-utils";
import Glass from "../assets/Glass.vue";
import Bottle from "../assets/Bottle.vue";

defineProps<{
  pricePerGlass?: number;
  glassVolume?: number;
}>();
</script>

<style scoped>

</style>
