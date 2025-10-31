<script setup>
import {computed, inject} from "vue";
import {cityProvide} from "../constants.js";
import IconLocation from "./icons/IconLocation.vue";
import IconCloud from "./icons/weather/IconCloud.vue";
import IconSun from "./icons/weather/IconSun.vue";
import IconRain from "./icons/weather/IconRain.vue";

const props = defineProps({weather: Object});
const city = inject(cityProvide)

function createDate() {
  let day = new Date(1610685149 * 1000).toLocaleString("ru", {weekday: "long"});
  day = capitalLetter(day)
  return day
}

function capitalLetter(word) {
  if (typeof word === 'string') {
    word = word.charAt(0).toUpperCase() + word.slice(1);
    return word
  }
}

let checkingWeather = computed(() => {
  if (props.weather) {
    return props.weather
  }
})
</script>

<template>
  <div class="left-panel">
    <div class="image"></div>
    <div>
      <h2> {{ createDate() }}</h2>
      <p>
        <IconLocation/>
        {{ city }}
      </p>
    </div>

    <p>
      <IconCloud v-if="checkingWeather.icon ==='04n' || checkingWeather.icon ==='03n' "/>
      <IconSun v-if="checkingWeather.icon ==='01n'"/>
      <IconRain v-if=" checkingWeather.icon==='10n'"/>
      {{ capitalLetter(checkingWeather.description) }}
    </p>
  </div>
</template>

<style scoped>
.left-panel {
  position: relative;
  border-radius: 30px;
  padding: 30px;
  height: 420px;
  max-width: 360px;
  width: 100%;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  @media (max-width: 1024px) {
    border-radius: 20px;
    height: 520px;
  }
  @media (max-width: 768px) {
    padding: 20px;
    border-radius: 10px;
    height: 360px;
  }

  & h2 {
    font-size: 28px;
    margin-bottom: 16px;
    @media (max-width: 1024px) {
      font-size: 24px;
      margin-bottom: 14px;
    }
  }

  & p {
    display: flex;
    align-items: center;
    column-gap: 4px;
    font-size: 22px;
    @media (max-width: 1024px) {
      font-size: 18px;
    }
  }
}

.image {
  width: 100%;
  height: 100%;
  opacity: 0.6;
  position: absolute;
  background: url("../assets/images/city.jpeg") center no-repeat;
  background-size: cover;
  left: 0;
  top: 0;
  z-index: -1;
  filter: blur(2px);
}

</style>