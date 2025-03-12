<template>
  <template v-if="error">
    <ErrorCard :retry="fetchEvents"
      >Could not load events at the moment. Please try again.</ErrorCard
    >
  </template>
  <template v-else>
    <section class="grid grid-cols-1 md:grid-cols-2 gap-8">
      <template v-if="!eventsLoading">
        <template v-if="events.length">
          <EventCard
            v-for="event in events"
            :key="event.id"
            :title="event.title"
            :when="event.date"
            :description="event.description"
            @register="handleRegisrtation(event)"
          />
        </template>
        <template v-else>
          <div class="col-span-2 text-center text-gray-500">No events yet!</div>
        </template>
      </template>
      <template v-else>
        <LoadingEventCard v-for="i in 4" :key="i" />
      </template>
    </section>
  </template>
</template>

<script setup>
import { onMounted, ref } from 'vue'

import useBookings from '@/composables/useBookings'
import EventCard from '@/components/EventCard.vue'
import LoadingEventCard from '@/components/LoadingEventCard.vue'
import ErrorCard from '@/components/ErrorCard.vue'

const { handleRegisrtation } = useBookings()

const events = ref([])
const eventsLoading = ref(false)
const error = ref(null)

const fetchEvents = async () => {
  eventsLoading.value = true
  error.value = null
  try {
    const response = await fetch('http://localhost:3001/events')
    events.value = await response.json()
  } catch (e) {
    error.value = e
  } finally {
    eventsLoading.value = false
  }
}

onMounted(() => {
  fetchEvents()
})
</script>

<style lang="scss" scoped></style>
