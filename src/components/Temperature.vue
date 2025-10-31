<script setup>
import IconTemp from "./icons/weather/IconTemp.vue";
import IconFeelsLike from "./icons/weather/IconFeelsLike.vue";
import IconTempMin from "./icons/weather/IconTempMin.vue";
import IconTempMax from "./icons/weather/IconTempMax.vue";
import {computed} from "vue";

const props = defineProps({temp: Object})
let filterTemp = computed(() => {
  if (props.temp !== undefined && props.temp !== null) {
    return [
      {
        icon: IconTemp,
        label: 'Температура',
        temp: props.temp.main.temp.toFixed(0) + ' °C'
      },
      {
        icon: IconTempMax,
        label: 'Температура максимальная',
        temp: props.temp.main.temp_max.toFixed(0) + ' °C'
      },
      {
        icon: IconTempMin,
        label: 'Температура минимальная',
        temp: props.temp.main.temp_min.toFixed(0) + ' °C'
      },
      {
        icon: IconFeelsLike,
        label: 'Ощущается',
        temp: props.temp.main.feels_like.toFixed(0) + ' °C'
      },
    ]
  }
})

</script>

<template>
  <div class="temperature">
    <template v-for="item in filterTemp">
      <div class="information" :title="item.label">
        <component :is="item.icon"/>
        <strong>{{ item.temp }}</strong>
      </div>
    </template>
  </div>
</template>

<style scoped>
.temperature {
  display: grid;
  grid-template-columns: 82px 82px 82px 82px;
  justify-content: space-between;
  @media (max-width: 1024px) {
    grid-template-columns: 82px 82px;
    justify-content: space-evenly;
    row-gap: 14px;
  }

  & .information {
    padding: 16px;
    border-radius: 8px;
    background: var(--color-bg-card);
    display: flex;
    flex-direction: column;
    align-items: center;
    row-gap: 6px;
    transition: 0.5s ease;

    &:hover {
      background: var(--color-primary);
      color: var(--color-primary-inverted);
    }
  }
}
</style>