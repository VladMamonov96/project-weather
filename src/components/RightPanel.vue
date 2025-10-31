<script setup>
import Stat from "./Stat.vue";
import CitySelect from "./CitySelect.vue";
import Error from "./Error.vue";
import {computed} from "vue";
import Temperature from "./Temperature.vue";

const props = defineProps({
  error: String,
  data: Object,
  getCity: Function,
})

let dataModified = computed(() => {
  if (props.data !== undefined && props.data.value !== null && props.error.length === 0) {
    return [
      {
        label: "Влажность",
        stat: props.data.main.humidity + ' %'
      },
      {
        label: "Облачность",
        stat: props.data.clouds.all + ' %'
      },
      {
        label: "Ветер",
        stat: props.data.wind.speed + ' м/ч'
      }
    ];
  } else {
    return []
  }

})
</script>

<template>
  <div class="right-panel">
    <Error :error="props.error"/>
    <Stat v-for="(item, index) in dataModified" :key="index" v-bind="item"/>
    <Temperature :temp="data"/>
    <CitySelect @select-city="getCity"/>
  </div>
</template>

<style scoped>
.right-panel {
  display: flex;
  flex-direction: column;
  row-gap: 12px;
  background: var(--color-bg-main);
  padding: 30px;
  border-top-right-radius: 25px;
  border-bottom-right-radius: 25px;
  max-width: 460px;
  width: 100%;
  @media (max-width: 1024px) {
    max-width: 360px;
  }
  @media (max-width: 768px) {
    border-radius: 10px;
    padding: 20px;
  }
}
</style>