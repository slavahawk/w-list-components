<template>
  <div v-if="pricePerBottle" class="flex gap-2 items-center">
      <Bottle />
      <span>{{ formatPrice(pricePerBottle) }}</span>
      <sub v-if="bottleVolume" class="text-xs items-end">{{ bottleVolume }} мл</sub>
  </div>
</template>

<script setup lang="ts">
import { formatPrice } from "w-list-utils";
import Glass from "../assets/Glass.vue";
import Bottle from "../assets/Bottle.vue";

defineProps<{
  pricePerBottle?: number;
  bottleVolume?: number;
}>();
</script>

<style scoped>
</style>
