<script setup></script>

<template>
  <header>
    <button @click="$emit('exit')" id="exit">
      <div>X</div>
      <div>EXIT</div>
    </button>
  </header>
</template>

<style scoped lang="scss">
header {
  background: var(--color-background);
  display: flex;
  justify-content: end;
}
#exit {
  display: flex;
  gap: 0.6rem;
  margin: 0.8rem 3rem;
  background-color: var(--color-background-dark);
  border-radius: 5px;
  border-style: none;
  color: white;
  padding: 7px 20px;
}
#exit div {
  font-size: 0.8rem;
}
</style>
