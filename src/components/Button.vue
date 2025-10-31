<template>
  <button class="button">
    <slot name="icon"/>
    <slot name="default"/>
  </button>
</template>

<style scoped>
.button {
  display: flex;
  background: var(--grabient);
  border: none;
  border-radius: 10px;
  padding: 14px;
  font-family: var(--font) sans-serif;
  font-size: 18px;
  font-weight: 600;
  height: 51px;
  color: var(--color-primary);
  cursor: pointer;
  justify-content: center;
}

.button:hover {
  background: var(--grabient-inverted);
}

</style>