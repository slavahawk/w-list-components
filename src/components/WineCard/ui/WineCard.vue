<template>
  <div class="wine-detail">
    <img :src="img" alt="Wine Image" class="wine-image"/>
    <div class="wine-info">
      <h3 class="text-xl mb-4">{{ name }}</h3>
      <p class="mb-4" style="color: var(--primary-color)">
        {{ country }},
        {{ region }}
      </p>
      <p class="mb-4" style="white-space: pre-line;">
        {{ organoleptic }}
      </p>
      <slot/>
      <p class="mb-4" v-if="showVintage(categoryId)">
        <strong>Год урожая:</strong> {{ vintage }}
      </p>
      <p class="mb-4">
        <strong>Сорта винограда: </strong>
        <span v-for="(g, index) in grapes" :key="g">
          {{ g }}<span v-if="index < grapes.length - 1">, </span>
        </span>
      </p>

      <p class="mb-4">
        <strong>Категория:</strong>
        {{ category }}
      </p>
      <p class="mb-4">
        <strong>Цвет:</strong> {{ colour }}
      </p>
      <p class="mb-4">
        <strong>Алкоголь:</strong>
        {{ alcoholByVolume }} %
      </p>
      <p class="mb-4">
        <strong>Тип сахара:</strong>
        {{ sugarType }}
      </p>
      <p style="white-space: pre-line;">{{interestingFacts}}</p>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { showVintage } from 'w-list-utils';
import { WineCategoryEnum } from 'wlist-types';

defineProps<{
  img: string;
  name: string
  country: string
  region: string
  grapes: string[]
  interestingFacts: string
  vintage: string | number
  category: string
  categoryId: WineCategoryEnum
  colour: string
  alcoholByVolume: number
  sugarType: string
  organoleptic: string
}>();
</script>

<style scoped lang="scss">
.wine-detail {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
  position: relative;

  @media screen and (max-width: 660px) {
    display: block;
    overflow-y: scroll;
  }
}

.wine-image {
  position: sticky;
  top: 0;
  margin: 0 auto;
  max-height: 100%;
  height: 100%;
  min-height: 228px;
  display: block;

  @media screen and (max-width: 660px) {
    position: relative;
    top: auto;
    height: 100%;
    display: block;
    margin: 0 auto 24px;
    max-height: 40vh;
  }
}

.wine-info {
  overflow-y: scroll;
  @media screen and (max-width: 660px) {
    overflow-y: hidden;
  }
}
</style>
