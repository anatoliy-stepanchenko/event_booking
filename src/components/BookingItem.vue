<template>
  <SectionCard>
    <div class="flex justify-between">
      <div class="flex space-x-4">
        <p>{{ title }}</p>
        <div>
          <component
            :is="icon"
            :class="{ 'animate-spin text-orange-600': pending }"
            class="text-green-600"
          />
        </div>
      </div>
      <BaseButton variant="danger" @click="$emit('cancelled')">Cancel</BaseButton>
    </div>
  </SectionCard>
</template>

<script setup>
import SectionCard from '@/components/SectionCard.vue'
import BaseButton from '@/components/BaseButton.vue'

import { LoaderCircle, Check } from 'lucide-vue-next'
import { computed } from 'vue'

const props = defineProps({
  title: String,
  status: String,
})

const pending = computed(() => props.status === 'pending')
const icon = computed(() => (pending.value ? LoaderCircle : Check))

defineEmits(['cancelled'])
</script>

<style lang="scss" scoped></style>
