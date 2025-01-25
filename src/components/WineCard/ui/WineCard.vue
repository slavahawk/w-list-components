<template>
  <div class="wine-detail">
    <img :src="originalImagePath" alt="Wine Image" class="wine-image"/>
    <div class="wine-info">
      <h3 class="text-xl mb-4">{{ name }}</h3>
      <p class="mb-4" style="color: var(--primary-color)">
        {{ country }},
        {{ region }}
      </p>
      <p class="mb-4">{{ interestingFacts }}</p>

      <slot/>
      <p class="mb-4">
        <strong>Год урожая:</strong> {{ vintage }}
      </p>
      <p class="mb-4">
        <strong>Сорта винограда: </strong>
        <span v-for="(g, index) in grapes" :key="g">
          {{ g }}
          <span v-if="index < grapes.length - 1">, </span>
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
        <strong>Алкогольное содержание:</strong>
        {{ alcoholByVolume }} %
      </p>
      <p class="mb-4">
        <strong>Уровень сахара:</strong>
        {{ sugarType }}
      </p>
      <p>
        <strong>Органолептические характеристики:</strong>
        {{ organoleptic }}
      </p>
    </div>
  </div>
</template>

<script lang="ts" setup>
defineProps<{
  originalImagePath: string;
  name: string
  country: string
  region: string
  grapes: string[]
  interestingFacts: string
  vintage: string | number
  category: string
  colour: string
  alcoholByVolume: number
  sugarType: string
  organoleptic: string
}>();
</script>

<style scoped>
.wine-detail {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
  position: relative;
}

.wine-image {
  position: sticky;
  top: 0;
  margin: 0 auto;
  max-height: calc(100vh - 200px);
}

.wine-info {
  overflow: scroll;
}
</style>
