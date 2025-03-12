<template>
  <SectionCard>
    <div class="flex flex-col items-center space-y-4">
      <div class="text-red-500"><slot></slot></div>
      <BaseButton @click="retry" v-if="retry">Retry now</BaseButton>
    </div>
  </SectionCard>
</template>

<script setup>
import SectionCard from '@/components/SectionCard.vue'
import BaseButton from './BaseButton.vue'

defineProps({
  retry: {
    type: Function,
    required: false,
  },
})
</script>

<style lang="scss" scoped></style>
