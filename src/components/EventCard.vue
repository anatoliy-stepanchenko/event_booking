<template>
  <SectionCard>
    <template #header>{{ title }}</template>
    {{ when }}
    <template #footer>
      <div class="space-y-4">
        <p>{{ description }}</p>
        <div class="flex justify-end">
          <BaseButton @click="$emit('register')"> Register</BaseButton>
        </div>
      </div>
    </template>
  </SectionCard>
</template>

<script setup>
import BaseButton from '@/components/BaseButton.vue'
import SectionCard from '@/components/SectionCard.vue'
defineProps({
  title: String,
  when: String,
  description: String,
})

defineEmits(['register'])
</script>

<style lang="scss" scoped></style>
