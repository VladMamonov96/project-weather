<script setup>
import Button from "./Button.vue";


let props = defineProps(['placeholder', 'value'])
let emit = defineEmits(['clickButton', 'update:value'])
let data = defineModel({type: String, required: true})

function clickButton() {
  emit('clickButton', props)
}
</script>

<template>
  <label class="label" for="">
    <input :placeholder="props.placeholder" v-focus v-model="data" @keyup.enter="clickButton"/>
    <Button @click="clickButton">Сохранить</Button>
  </label>
</template>

<style scoped>
.label {
  display: flex;
  gap: 12px;
  @media (max-width: 768px) {
    flex-direction: column;
  }

  & input {
    color: var(--color-primary);
    border: none;
    padding: 15px 20px;
    font-size: 18px;
    border-radius: 10px;
    background: var(--color-bg-card);
    box-shadow: 1px 2px 4px 0 var(--color-bg-main);
    width: 100%;

    &::placeholder {
      color: var(--color-text-placeholder);
    }

    &:focus {
      outline: 2px solid rgba(144, 217, 224, 0.90);
    }
  }
}
</style>