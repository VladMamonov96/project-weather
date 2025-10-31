<script setup>

import Button from "./Button.vue";
import IconLocation from "./icons/IconLocation.vue";
import InputBlock from "./InputBlock.vue";
import {inject, ref} from "vue";
import {cityProvide} from "../constants.js";


let isEdited = ref(false)
const city = inject(cityProvide)
let valueInput = ref(city.value)

function select() {
  isEdited.value = false
  valueInput.value = String(valueInput.value).charAt(0).toUpperCase() + String(valueInput.value).slice(1);
  city.value = valueInput.value;
}

function edit() {
  isEdited.value = true
}

</script>

<template>
  <Button v-if="!isEdited" @click="edit">
    <template #icon>
      <IconLocation/>
    </template>
    Изменить город
  </Button>
  <template v-else>
    <InputBlock @click-button="select" v-model="valueInput"   placeholder="Ведите город"/>
  </template>
</template>

<style scoped>

</style>