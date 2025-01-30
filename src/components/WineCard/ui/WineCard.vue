<template>
  <div class="wine-detail">
    <img :src="img" alt="Wine Image" class="wine-image"/>
    <div class="wine-info">
      <h3 class="text-xl mb-4">{{ name }}</h3>
      <p class="mb-4" style="color: var(--primary-color)">
        {{ country }},
        {{ region }}
      </p>
      <p class="mb-4">
        {{ organoleptic }}
      </p>
      <slot/>
      <p class="mb-4">
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
        <strong>Алкогольное содержание:</strong>
        {{ alcoholByVolume }} %
      </p>
      <p class="mb-4">
        <strong>Уровень сахара:</strong>
        {{ sugarType }}
      </p>
      <p>{{ interestingFacts }}</p>
    </div>
  </div>
</template>

<script lang="ts" setup>
defineProps<{
  img: string;
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

<style scoped lang="scss">
.wine-detail {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
  position: relative;

  @media screen and (max-width: 765px) {
      display: block;
      overflow-y: scroll;
  }
}

.wine-image {
  position: sticky;
  top: 0;
  margin: 0 auto;
  max-height: calc(100vh - 300px);

    @media screen and (max-width: 765px) {
    position: relative;
    top: auto;
    height: 100%;
    display: block;
      margin: 0 auto 24px;
  }
}

.wine-info {
  overflow-y: scroll;
      @media screen and (max-width: 765px) {
  overflow-y: hidden;
  }
}
</style>
