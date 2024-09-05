<script setup>
import { twMerge } from 'tailwind-merge'
defineProps(['courseName', 'activeName', 'openWindow', 'id', 'link', 'className'])
defineEmits(['openWindow']) //define function or action
</script>

<template>
  <button
    :class="
      twMerge(
        'flex flex-1 items-center justify-center gap-2 rounded-md font-bold text-xs md:text-sm uppercase tracking-wide outline-0 transition active:translate-y-0.5 p-4 bg-spacecadet text-saffron md:w-full w-3/4 justify-self-center',
        className
      )
    "
    @click="$emit('openWindow', id, link)"
    :id="{ active: courseName == activeName }"
  >
    <p>{{ id }}. {{ courseName }}</p>
  </button>
</template>
