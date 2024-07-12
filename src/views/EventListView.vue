<script setup lang="ts">
import EventCard from '@/components/EventCard.vue'
import ShowName from '@/components/ShowName.vue'
// import ShowName from '@/components/ShowName.vue'
import type { Event } from '@/types'
import { ref, onMounted } from 'vue'
import EventService from '@/services/EventService'

const events = ref<Event[] | null>(null)

onMounted(() => {
  EventService.getEvents()
    .then(({data}: {data: Event[]}) => {
      //console.log(response.data)
      events.value = data
    })
    .catch((error) => {
      console.error('There was an error!', error)
    })
})
</script>

<template>
  <h1>Events For Good</h1>
  <!-- new element-->
  <div class="home">
    <EventCard v-for="event in events" :key="event.id" :event="event" />
    <ShowName v-for="event in events" :key="event.category" :event="event" />
  </div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
