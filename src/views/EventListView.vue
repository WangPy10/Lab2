<script setup lang="ts">
import EventCard from '@/components/EventCard.vue'
import EventCategoryOrganizer from '@/components/EventCategoryOrganizer.vue'
import type { Event } from '@/types'
import { ref, onMounted } from 'vue'
import EventService from '@/services/EventService'

const events = ref<Event[]>([])

onMounted(() => {
  EventService.getEvents()
    .then((response) => {
      events.value = response.data
    })
    .catch((error) => {
      console.error('There was an error!', error)
    })
})
</script>

<template>
  <h1>Events For Good</h1>
  <div class="events">
    <div v-if="events">
      <div v-for="event in events" :key="event.id" class="event-container">
        <EventCard :event="event" />
        <EventCategoryOrganizer :event="event" />
      </div>
    </div>
    <div v-else>Loading events...</div>
  </div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
