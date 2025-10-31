<script setup>
const {label = "Не задан", stat = "Не задан"} = defineProps({label: String, stat: String})
</script>

<template>

  <div class="state">
    <strong class="state-name">{{ label }}</strong>
    <span class="state-value">{{ stat }}</span>
  </div>
</template>

<style scoped>
.state {
  display: flex;
  justify-content: space-between;
  gap: 16px;
  font-size: 28px;
  @media (max-width: 1024px) {
    font-size: 24px;
  }
  @media (max-width: 768px) {
    font-size: 20px;
    gap: 8px;
  }
}
</style>