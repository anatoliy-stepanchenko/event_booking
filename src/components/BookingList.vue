<template>
  <template v-if="error">
    <ErrorCard :retry="fetchBookings">Failed to fetch bookings.</ErrorCard>
  </template>
  <template v-else>
    <section class="grid grid-cols-1 gap-4">
      <template v-if="!bookingsLoading">
        <BookingItem
          v-for="booking in bookings"
          :key="booking.id"
          :title="booking.eventTitle"
          :status="booking.status"
          @cancelled="cancelBooking(booking.id)"
        />
      </template>
      <template v-else>
        <LoadingBookingCard v-for="i in 4" :key="i" />
      </template>
    </section>
  </template>
</template>

<script setup>
import { onMounted } from 'vue'

import useBookings from '@/composables/useBookings.js'
import BookingItem from '@/components/BookingItem.vue'
import LoadingBookingCard from '@/components/LoadingBookingCard.vue'
import ErrorCard from '@/components/ErrorCard.vue'

const { bookings, bookingsLoading, error, fetchBookings, cancelBooking } = useBookings()

onMounted(() => {
  fetchBookings()
})
</script>

<style lang="scss" scoped></style>
