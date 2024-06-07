<script setup>
defineProps(['courseName', 'activeName', 'openWindow', 'id', 'link'])
defineEmits(['openWindow'])
</script>

<template>
  <button @click="$emit('openWindow', id, link)" :id="{ active: courseName == activeName }">
    {{ courseName }}
  </button>
</template>

<style scoped lang="scss">
button {
  background: var(--color-background);
  font-weight: bold;
  border: none;
  border-radius: 10px;
  padding: 0.7rem 2rem;
  margin: 0.25rem;
  color: var(--color-accent);
  line-height: 1.5;
  min-height: 4rem;
  width: 30rem;

  @media only screen and (max-width: 1024px) {
    font-size: $m-2;
    width: 20rem;
  }
}
button:first-child,
button:last-child {
  grid-column: 1 / span 2;
  justify-self: center;
  margin: 0.25rem;
  padding: 0 10rem;
  @media only screen and (max-width: 1024px) {
    padding: 0.7rem 2rem;
    margin: 0.5rem;
  }
  @media only screen and (max-width: 550px) {
    margin-bottom: 0.25em;
  }
}
</style>
