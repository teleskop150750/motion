<script setup lang="ts">
import { Motion, useAnimations } from '../../../index.ts'
import { onMounted, ref } from 'vue'

const rotate = ref(500)

const animations = useAnimations()
onMounted(() => {
  setTimeout(() => {
    animations.stop()
    // eslint-disable-next-line no-console
    console.log('motion stopped')
  }, 500)
})
</script>

<template>
  <Motion
    :keyframes="{
      rotate: `${rotate}deg`,
      backgroundColor: '#FFD700',
    }"
    :options="{
      duration: 1,
    }"
  />

  <div
    :style="{
      marginTop: '50px',
    }"
  >
    <button @click="rotate += 20">
      Rotate
    </button>
  </div>

  <Motion
    :initial="{ opacity: 0, x: -50 }"
    :in-view="{
      opacity: 1,
      x: 0,
      transition: {
        delay: 0.5,
        easing: [0.17, 0.55, 0.55, 1],
        duration: 0.9,
      },
    }"
  >
    <p>
      Lorem Ipsum
    </p>
  </Motion>
</template>
