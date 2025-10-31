<script setup>
import LeftPanel from "./components/LeftPanel.vue";
import RightPanel from "./components/RightPanel.vue";
import {onMounted, provide, ref, watchEffect} from "vue";
import {API_ENDPOINT, cityProvide} from "./constants.js";

let city = ref('Moscow')
const data = ref()
const error = ref('')
const weather = ref({})

provide(cityProvide, city)

async function getCity(city) {
  const params = new URLSearchParams({
    q: city,
    appid: '7226e6e009e839de9f07a9112d003d89',
    lang: 'ru'
  })
  const res = await fetch(`${API_ENDPOINT}/weather?units=metric&${params.toString()}`)
  data.value = await res.json()
  weather.value = {
    description: data.value.weather[0]['description'],
    icon: data.value.weather[0].icon,
  }
  if (res.status !== 200) {
    error.value = 'Город не найден'
  } else {
    error.value = ''
  }
}

watchEffect(() => {
  getCity(city.value)
})

onMounted(() => {
  getCity(city.value)
})
</script>

<template>
  <main class="main">
    <LeftPanel :weather="weather"/>
    <RightPanel :error="error" :data="data"/>
  </main>
</template>

<style scoped>
.main {
  display: flex;
  align-items: center;
  height: 100vh;
  justify-content: center;
  margin: 10px;
  @media (max-width: 768px) {
    height: 100%;
    row-gap: 10px;
    flex-direction: column;
  }
}
</style>
