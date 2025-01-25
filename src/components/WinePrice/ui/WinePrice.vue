<template>
  <div class="grid justify-self-start" style="grid-template-columns: 1fr 1fr;">
    <div>
      <div v-if="pricePerGlass" class="flex gap-2 items-center widthItem">
        <Glass />
        <span>{{ formatPrice(pricePerGlass) }}</span>
        <sub v-if="glassVolume" class="text-xs items-end">{{ glassVolume }} мл</sub>
      </div>
    </div>
    <div>
      <div v-if="pricePerBottle" class="flex gap-2 items-center widthItem">
        <Bottle />
        <span>{{ formatPrice(pricePerBottle) }}</span>
        <sub v-if="bottleVolume" class="text-xs items-end">{{ bottleVolume }} мл</sub>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { formatPrice } from "w-list-utils";
import Glass from "../assets/Glass.vue";
import Bottle from "../assets/Bottle.vue";

defineProps<{
  pricePerGlass?: number;
  pricePerBottle?: number;
  bottleVolume?: number;
  glassVolume?: number;
}>();
</script>

<style scoped>
.widthItem {
  width: 150px
}
</style>
